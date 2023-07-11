# trabalhoredes
# Envio de arquivos utlizando o Docker

Para utilizar a aplicação é necessário possuir previamente instalado em suas máquinas o Docker e a versão 3.X do Python. Segue o passo a passo:

1. Execute a imagem do Servidor em uma máquina. Como ele não encontrará localmente, o arquivo será baixado:
   ```bash
   docker run -it --rm --network=host michelom/server:v1 /bin/bash
   ```
2. Agora você terá acesso ao container, portanto, nesta mesma máquina, execute o servidor através do seguinte comando:
   ```bash
   python3 server.py
   ```
OBS: A partir de então o servidor estará online e pronto aguardando novas conexões.
   
3. Precisaremos então executar a imagem do client em outra máquina. Novamente, ele não encontrará localmente e o arquivo será baixado através do código:
   ```bash
   docker run -it --rm --network=host michelom/client:v2 /bin/bash
   ```
4. Novamente, você terá acesso ao container, porém agora do client. Nesta máquina, execute o client através do seguinte comando:
   ```bash
   python3 client.py
   ```
   A partir de então o cliente irá solicitar o IP da máquina onde foi baixada e executada a imagem do servidor.
   
5. Agora na máquina que será utilizada como cliente, indique o IP do servidor.
   ```bash
   Exemplo: "192.168.128.34"
   ```
6. Indique o nome de um arquivo que deseja enviar para o servidor. Como exemplo, colocamos dois arquivos em python dentro do container do cliente, sendo eles:
   ```bash
   imagem.py
   instalador.py
   ```
7. Após isso, aparecerá uma mensagem de arquivo recebido no servidor.
8. Caso deseje enviar mais de um arquivo, deixe o servidor rodando e execute novamente a imagem do cliente.
9. Os arquivos recebidos no server podem ser vistos digitando o comando ls dentro do container.
10. Os arquivos recebidos terão nomes "Arquivo-recebido-X" onde X será a ordem na qual ele foi enviado. Ex: Arquivo-recebido-1, Arquivo-recebido-2, etc...

