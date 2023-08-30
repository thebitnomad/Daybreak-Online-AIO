# 💥 Daybreak-Online- All In One Repo
Um repositório abrangente para o Daybreak Online, contendo diversas ferramentas, bancos de dados e arquivos necessários para configurar o servidor.

## App preview
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/c67e4032-a153-419c-9692-4dfb16855ed0)

## ℹ️ Recursos Disponíveis

- [DayBreak GMTools IIS APP](https://github.com/thebitnomad/DayBreak-GMTools)
- [DayBreak GMTools database](https://drive.google.com/file/d/1uhB7LuhSphhOUIDReDOvMkKYn6aaTcfC/view?usp=drive_link)
- [DayBreak Game Database](https://drive.google.com/file/d/1nGPV9_9Tu5djmYOCMifNOs-2VQDNKOLV/view?usp=drive_link)
- [DayBreak Game log "required"](https://drive.google.com/file/d/1GlXFgK0jBJ0AbPvV0x0HJr8u5GM4pFXb/view?usp=drive_link)
- [DayBreak eRating - CentOS x86 VMware](https://drive.google.com/file/d/1_o9YP16D0ZJZcKBL9eTtllVioFw5B6v3/view?usp=drive_link)
  - usuário: root
  - senha: ivanglobalgames
- [DayBreak GameServer - CentOS x64 VMware](https://drive.google.com/file/d/17rorms6ihLPh3ScZ0P6JTaTk2MQe7HFz/view?usp=drive_link)
  - usuário: root
  - senha: ivanglobalgames
- [DayBreak Game Client](https://drive.google.com/file/d/1B7Mx6gyQeBXmqtlSbVgdO2RjoAxwAaJG/view?usp=drive_link)
- [VMWare WorkStation](https://drive.google.com/file/d/1BTE5S12eX20QfLxIrNRaOOQaZ3yJ-6CM/view?usp=drive_link)
- [MySQL](https://downloads.mysql.com/archives/get/p/23/file/mysql-5.5.62-winx64.msi)
- [Netframework 2.0](https://www.microsoft.com/pt-br/download/confirmation.aspx?id=6041)

## 📝 Instruções

### 1. Instalação

- Instale o IIS no seu Windows.
- Suba a pasta `masterweb`.
- Habilite a opção "Aplicativos de 32 bits = True".
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/cd2687cf-a29e-4678-b8c7-22d645fdb12d)
- Altere o `modo pipeline gerenciado` para Clássico
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/2b94e8a4-2318-4b79-af94-18cf96a64986)

- Importe os seguintes bancos de dados para o MySQL 5.5: `master.sql`, `daybreak_104001`, `daybreaklog_104001`.
- Altere as configurações do arquivo `masterweb/App_Data/MasterSqlMap.config` com seu IP interno, usuário e senha do banco de dados.
`<dataSource name="master" connectionString="Server=127.0.0.1;Port=3306;Database=master;Uid=root;Pwd=password;Allow User Variables=True;Character Set=utf8;" />`
- Copie a Connection String a partir do " `Server=127.0.0.1;Port=3306;Database=master;Uid=root;Pwd=password;Allow User Variables=True;Character Set=utf8;`
- Utilize o [dbcrypto](https://drive.google.com/file/d/1ws-09pjo5N7151SdwjtFdQmqnTkEqZz-/view?usp=drive_link) para criptografar a Connection String.
- Altere a linha DBConnectionString do arquivo `masterconfig.xml` utilizando a Connection String criptografada.
- Altere a senha do usuário `ivangod` no banco de dados `master`, utilizando uma criptografia MD5. Você pode utilizar uma ferramenta como [MD5HashGenerator](https://www.md5hashgenerator.com/).
- Senha = (User+Senha) exemplo; usuario é ivangod, senha é 123test, logo, o md5 será `3377e95f44105286e6a5b63291a96d93` (ivangod123test)
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/0ceb9f26-da01-40e5-8cc6-7399cafdc20c)

### 2. Configuração do Servidor

- Suba o VMWare `erating`.
- Suba o VMWare `GameServer`.
- Vá até o diretório `/sdetector/sat_detector.cfg` na maquina do GameServer. 
- A string se resume em IP "Invertido e Convertido em decimal" / PORTA / PORTA. Você deve alterar apenas o IP, apontando para o GMTools. Utilize uma ferramenta como [IPAddressGuide](https://www.ipaddressguide.com/ip) para converter o IP para decimal. Por exemplo, o IP `192.168.18.6` invertido; `6.18.168.192` convertido para decimal é `101886144`, portanto, a string completa será `101886144:9999:81920`.
- Após acessar o Saturn Master, Clique com o botão direito do mouse na página e selecione `traduzir para português` ou qualquer outro idioma de sua preferência.
- Clique em `Gerenciamento físico de maquinas` e adicione o servidor do banco, e o Game server conforme exemplos; 
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/741dba86-1620-4f51-afe2-5a838c467a24)
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/4f43c303-8a10-42a8-8232-83f33d34783f)
- No servidor do GameServer, adicione esses dois caminhos; `/home/sdetector/sdetector` e `/home/server/dbserver` "o nome muda conforme a tradução"
  
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/4898bb47-2815-40cb-a4d5-3027b7fc7eda)
- Se a configuração estiver certa, a linha do GameServer que estava vermelha, vai ficar toda verde. PS: A linha do banco de dados permanece vermelha.
  
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/374b0518-dc35-4fc8-8058-4c938cd7bfda)

### 3. Iniciar GameServer
- Clique em `Gestão de serviços distritais` , `Adicionar um grupo de servidores` 
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/020b1886-4e78-4ab3-a180-ffd52cdfc0e6)
- Na Progressão do jogo, selecione `/home/server/dbserver` e Ok.
- Clique no icone de engrenagem, preencha os dados do seu banco de dados, IP, usuario e senha, desabilite o log, e opção de autenticação do erating; 
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/f46f07e3-67fb-41ee-b788-91fbf95da1e0)
![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/5496e722-fdc4-4987-ac96-938e683c9608)
- Após isso é só clicar em play; ![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/c74764fc-0307-451c-af43-44f416e62f16)
- Se a configuração estiver certa, a linha do Servidor que estava vermelha, vai ficar verde. após isso, alterar o `svrlist` na pasta do [DayBreak Game Client](https://drive.google.com/file/d/1B7Mx6gyQeBXmqtlSbVgdO2RjoAxwAaJG/view?usp=drive_link)

![image](https://github.com/thebitnomad/Daybreak-Online-AIO/assets/134553365/41f18fe8-32aa-4d11-92bc-54caae66f0a6)
- Coloque o IP do GameServer e verifique a porta utilizada na VM do mesmo, utilizando o comando `netstat -tulnp`



### 🙏 Apoie o Projeto

Considere fazer uma doação.

Qualquer valor é bem-vindo e apreciado!

Endereço da Carteira (BSC/ETHEREUM/POLYGON): `0x9EEEAF03f3e3993f5C9b1Be69df3Ca94120f2eF1`

**Observação**: Aceitamos doações em qualquer rede. Sinta-se à vontade para escolher a rede que for mais conveniente para você.

Agradecemos antecipadamente por seu generoso apoio. Com sua ajuda, podemos continuar aprimorando e expandindo o projeto!









