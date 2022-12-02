# TemaEscuroSQL
Como habilitar o tema escuro
![image](https://user-images.githubusercontent.com/58008758/205193870-eebfdfab-0714-4807-9b2d-f4b95f75bd17.png)

## Tema escuro do SSMS : Como Configurar
Embora não seja oficialmente suportado pela Microsoft, o tema Escuro está disponível no SQL Server Management Studio 2016, 17 e na versão 18, a mais recente.
O tema escuro ou Dark Mode tem sido muito popular entre administradores e desenvolvedores de bancos de dados SQL.

## Tema escuro do SSMS : Como Configurar
Embora não seja oficialmente suportado pela Microsoft, o tema Escuro está disponível no SQL Server Management Studio 2016, 17 e na versão 18, a mais recente.
O tema escuro ou Dark Mode tem sido muito popular entre administradores e desenvolvedores de bancos de dados SQL.

Para ativar o tema Escuro do SSMS, siga estas etapas simples.

## Feche o SSMS se estiver em execução. 
Execute qualquer editor de texto como administrador
Em nosso caso usamos, o  Bloco de Notas (Notepad) que pode ser usado para editar o arquivo de configuração do SSMS
O arquivo de configuração (ssms.pkgundef) está localizado nos seguintes locais:

### SSMS 2016
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio

### SSMS 17
C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Binn\ManagementStudio

### SSMS 18
C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE

4. Depois que o arquivo for aberto no editor de texto, Procure a Palavra “Dark” ou role para baixo e localize a seção do código no cabeçalho “Remove Dark theme”, adicione “//” (sem as aspas) no início da primeira linha, conforme mostrado em nossa aula e Salve o arquivo.

Depois de concluído, inicie o SQL Server Management Studio e o tema Cor escura estará disponível na caixa suspensa Cor do Tema.


# Resolvendo Problemas com atualização do SSMS versus Tema Escuro
A cada atualização da última versão do SSMS o arquivo de configuração (ssms.pkgundef) retornará aos padrões do SQL Server. 
Ou seja, o upgrade substituirá o ajuste que fizemos anteriormente e o tema Escuro não estará mais disponível nas opções.

Em vez de executar novamente as mesmas etapas para ativar o tema Escuro do SSMS sempre que houver uma atualização do Management Studio, podemos executar um script PowerShell e alcançar o mesmo resultado só que com alguns cliques.

Para isso, executamos o PowerShell como administrador, clique em Iniciar , digite PowerShell, clique com o botão direito do mouse em Windows PowerShell e escolha Executar como administrador.

Dependendo da versão do SSMS, copie o script apropriado na área de transferência, cole-o no PowerShell e pressione Enter para executá-lo:

## SSMS 2016
powershell -Command “(gc ‘C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio\ssms.pkgundef’) -replace ‘\[\`$RootKey\`$\\Themes\\{1ded0138-47ce-435e-84ef-9ec1f439b749}\]’, ‘//[`$RootKey`$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}]’ | Out-File ‘C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio\ssms.pkgundef'”

## SSMS 17
powershell -Command “(gc ‘C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Binn\ManagementStudio\ssms.pkgundef’) -replace ‘\[\`$RootKey\`$\\Themes\\{1ded0138-47ce-435e-84ef-9ec1f439b749}\]’, ‘//[`$RootKey`$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}]’ | Out-File ‘C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Binn\ManagementStudio\ssms.pkgundef'”

## SSMS 18
powershell -Command “(gc ‘C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.pkgundef’) -replace ‘\[\`$RootKey\`$\\Themes\\{1ded0138-47ce-435e-84ef-9ec1f439b749}\]’, ‘//[`$RootKey`$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}]’ | Out-File ‘C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.pkgundef'”

![image](https://user-images.githubusercontent.com/58008758/205193158-fa8ff884-6930-4202-8a1c-565957d653af.png)


# *Não haverá mensagem de retorno de que a operação foi bem-sucedida, exceto o cursor piscando em uma nova linha.*

Após a conclusão de um desses métodos, inicie o SSMS e altere o tema para escuro.

Detalhe: Como mencionamos anteriormente, o tema Escuro do SSMS não é oficialmente suportado e provavelmente nunca será, o que é uma pena.
Por isso que está desativado por padrão. 
Pode haver alguns desvios visuais, por exemplo, fundo branco no Pesquisador de objetos, grade Resultados, etc.
