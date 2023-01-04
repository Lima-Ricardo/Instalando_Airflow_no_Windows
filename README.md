# Instalando_Airflow_no_Windows
Guia passo a passo de innstalação do Airflow no Windows usando o Docker

Instalando o Docker Desktop

Passo 01: Instale o Windows Terminal, (Foto 01) ele pode ser baixado da Microsoft Store e execute-o como administrador.
Nota: Se a sua versão do SO for o Win 11 Pro, basta apenas executar o powershell como administrador.

Passo 02: Execute o comando abaixo no Windows Terminal/PowerShell como Admin: 
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

Passo 03: Execute o segundo comando comando abaixo no Windows Terminal/PowerShell como Admin:
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Passo 04: Reinicie o computador

Passo 05: faça o Download e instale a iso do Linux kernel update package:
Site para download: https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

Passo 06: Instale o docker:
Tutorial: https://docs.docker.com/docker-for-windows/install/


========================================================================================================================================================================================


Instalando e criando o container do Apache Airflow

Passo 01: Crie uma Pasta chamada airflow-docker (tudo minúsculo, caso contrário dará erro no PowerShell)
Nota: Lembre se de listar esse diretório toda vez antes de rodar qualquer comando do powershell caso contrário dará erro.

Passo 02: Dentro da pasta airflow-docker mais outras 3 chamadas: dags, logs, plugins (tudo minúculo também foto 02)

Passo 03: Abra a IDE (VsCode ou Pycharm) e vá na pasta airflow-docker e crie um arquivo chamado: docker-compose.yaml

Passo 04: Entre no site 
https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html#fetching-docker-compose-yaml 

Passo 05: Procure pela opção "Fetching docker-compose.yaml", e logo abaixo clique em "To deploy Airflow on Docker Compose, you should fetch docker-compose.yaml." 
(foto 03) 

Passo 06: Copie todo o conteúdo da página e cole dentro do arquivo que você criou no editor de código docker-compose.yaml (foto 04)
Nota: O Arquivo criado está no passo 03 desta sessão. (Foto 05)


Passo 07: Abra o PowerShell como admin e vá até o diretório criado anteriormente e digite o seguinte comando:
docker-compose up airflow-init

Nota: O comando acima fará o sistema baixar e instalar toda a estrutura do Airflow e pode demorar um pouco, tudo vai depender da sua conexão e hardware.

Passo 08: Após a instalação digite o seguinte comando para fazer o docker subir o serviço:
docker-compose up 

Passo 09: Após o docker inicializar o container vá até o navegador e digite o seguinte endereço:
http://localhost:8080/home (endereço e porta padrão do airflow Foto 06) 

Nota: Se você fez tudo corretamente ele irá abrir a página do Airflow pedindo login e senha.
Login: airflow
Senha: airflow

Se quiser encerrar o Airflow basta ir no PowerShell e digitar: "docker-compose down" ou no dashboard e parar o serviço, no más agora é só criar as suas DAG's na pasta dags utilizando o editor de código de sua preferência.
