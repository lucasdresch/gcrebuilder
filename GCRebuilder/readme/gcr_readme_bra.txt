GameCube Rebuilder versão 1.1 da BSV (bsv798@gmail.com)
Compilado: setembro de 2016.
---------------------------------------------------------

A ferramenta GameCube Rebuilder (GCR a seguir) permite editar imagens do Nintendo GameCube.
Foi escrito com Visual C# v5.0 e, portanto, REQUER um Microsoft .NET Framework v4.5.2 ou mais recente instalado.
Você pode obtê-lo gratuitamente em https://www.microsoft.com/ru-ru/download/details.aspx?id=42642


Principais características:


- extrair (exportar) arquivos e pastas da imagem;
- substituir (importar) arquivos em imagem;
- criar (re/construir) uma nova imagem de trabalho a partir de arquivos de imagem extraídos anteriormente;
- limpe o lixo da imagem;
- alterar informações do banner;

e também:
- exporte o banner para um arquivo BMP do Windows (e edite-o em seu programa de edição favorito)
- importe-o de volta para a imagem (editada ou não).


---------------------------------------------------------
Comandos do menu "Imagem":
---------------------------------------------------------


Imagem -> Abrir...
----------------

- Abre uma imagem do Nintendo GC. Você pode escolher os formatos de arquivo *.iso, *.gcm ou "Todos os arquivos".
   (observe que .iso e .gcm são o mesmo tipo de imagens do GameCube.
   A diferença está apenas na extensão do arquivo).
   Ao abrir, o GCR lê todos os arquivos da imagem referentes às informações do arquivo "game.TOC".
   Se não conseguir encontrar algum arquivo necessário ou houver erros no arquivo game.toc,
   a imagem não será aberta.

Imagem -> Fechar
----------------

- Fecha a imagem atual e limpa todos os campos da GUI,
   permitindo que você abra outro através do menu "Imagem" ou "Root".

Imagem -> Limpar lixo
----------------

As imagens originais do GameCube têm dados aleatórios entre os arquivos adicionados
pela Nintendo por algum motivo estranho. Esses dados não afetam a jogabilidade de forma alguma
(não temos certeza disso, mas todas as imagens GC "limpas" funcionam perfeitamente).
O comando "wipe trash" substitui esses dados aleatórios por zero bytes e permite
alcançar taxas de compactação muito mais poderosas ao arquivar
(por exemplo, Rar'ing, Zip'ing) uma imagem "apagada".

- Este processo pode ser cancelado. (O menu "Limpar lixo" muda para "Cancelar" durante a limpeza.)
- Sua nova imagem compilada do GC não conterá esse tipo de lixo. Ele será apagado durante a compilação.


---------------------------------------------------------
Comandos do menu "raiz":
---------------------------------------------------------

Raiz -> Abrir...
----------------

- Abre imagem extraída anteriormente.

// Você pode extrair a imagem inteira para o seu HDD abrindo-a no GCR (Image->Open),
// clicando com o botão direito na pasta "Root" no campo "Estrutura" e escolhendo o comando "Exportar...".


Ao abrir, o GCR procura uma pasta "&&systemdata"
com os arquivos "iso.hdr", "apploader.ldr", "start.dol" e "game.toc".
Se não conseguir encontrar isso, não carregará a imagem extraída.
  
   *Veja o comando "Opções ->" Não usar game.toc "abaixo

Em seguida, ele lê o arquivo game.TOC e, se não conseguir encontrar os arquivos necessários, listados em game.toc,
sua imagem extraída não será aberta. Se houver alguns arquivos adicionais em sua pasta,
contendo a imagem extraída, o GCR irá simplesmente ignorá-los.

Raiz -> Salvar...
----------------

- Permite que você escolha um nome de arquivo para sua nova imagem antes de reconstruí-la.
   Você também pode escolher a extensão de arquivo *.iso ou *.gcm.
   Esta é apenas uma extensão, então não importa o que você escolher.
   Sua nova imagem estará totalmente funcional em qualquer caso.

Raiz -> Fechar
----------------

- Fecha a imagem extraída atual e limpa todos os campos da GUI,
   permite que você abra outro com o menu "Imagem" ou "Root".

Raiz -> Reconstruir
----------------

- Constrói uma nova imagem do GameCube em um arquivo, nomeado anteriormente através do comando "Salvar...".
   Durante a reconstrução, a posição de todos os arquivos na imagem é alinhada em 2.048 bytes.
   Posteriormente, isso PODE permitir que você importe arquivos um pouco maiores que os originais,
   à sua nova imagem reconstruída (sem reconstruí-la novamente).

   Após a reconstrução, você receberá um arquivo de imagem do GameCube totalmente funcional
   com tamanho de arquivo de 1,35 Gb (1459978240 bytes).
   Além disso, esta nova imagem já será eliminada do lixo.

---------------------------------------------------------
Comandos do menu "Opções":
---------------------------------------------------------

// Nota - esta opção só funciona ANTES de abrir uma imagem extraída (ROOT -> Open)
// Quando uma imagem normal do GC (Imagem -> Abrir) é aberta, essas opções são desativadas.


Opções -> Modificar arquivos do sistema
----------------

- Modifica os arquivos "iso.hdr" e "game.toc" na pasta "&&systemdata" enquanto constrói uma nova imagem.
   Use esta opção se quiser que esses arquivos sejam idênticos na pasta "Root" e na sua nova imagem.

Opções -> Não use 'game.toc'
----------------

- Com esta opção habilitada, o GCR ignora as informações do arquivo "game.toc".
   Isso significa que você pode, teoricamente, construir uma nova imagem GC funcional com QUALQUER arquivo na pasta "Root"
   (a pasta "&&systemdata" não deve conter arquivos ou pastas adicionais).
   A única limitação é o tamanho do arquivo da sua nova imagem.
   Deve ter exatamente 1,35 Gb (1459978240 bytes).
   Tudo que você precisa é de arquivos "apploader.ldr" e "start.dol" corretos na pasta "&&systemdata"
   para fazer essa imagem funcionar.

   // Use esta opção somente SE VOCÊ REALMENTE SABE o que está fazendo!!!
   // Se você não tiver certeza, deixe-os desativados.

---------------------------------------------------------
Menu "Ajuda":
---------------------------------------------------------

- Mostra uma breve informação sobre o GCR.

- Mostra parâmetros da interface de linha de comando.

---------------------------------------------------------
Campo "Detalhes da imagem":
---------------------------------------------------------

- Mostra informações da imagem. Isso NÃO pode ser alterado com GCR.

---------------------------------------------------------
Campo "Detalhes do banner":
---------------------------------------------------------

- Mostra informações do banner do jogo (arquivo "opening.bnr")
   (título do jogo, desenvolvedor, comentários e imagem do banner do jogo);
- permite editar todas as informações de texto, mas observe que cada campo de texto
   possui espaço limitado para digitação;
- permite exportar/importar imagem de banner de/para arquivo bitmap do Windows (BMP)
   (observe que o GCR suporta apenas arquivos BMP Windows RGB5A1 de 16 bits com tamanho de imagem
   de 96x32 pixels. Enquanto os canais alfa de exportação/importação serão ignorados).

Todas as alterações serão salvas na imagem somente após pressionar o botão "Salvar alterações".

---------------------------------------------------------
Campo "Estrutura":
---------------------------------------------------------

- Mostra toda a estrutura de diretórios/arquivos em sua imagem.

Você pode escolher um dos seguintes modos de visualização:

- "Tabela de nomes de arquivos", para ver os arquivos no estilo do Windows Explorer.
- “Tabela de endereços”, para ver como estão todos os arquivos localizados fisicamente dentro da imagem.

Se você abrir uma imagem do Gamecube compilada (ou uma imagem "normal"/"baixada em algum lugar") (Imagem->Abrir),
você poderá extrair e substituir arquivos e pastas nele:

  - Para extrair a imagem inteira do seu disco rígido, clique com o botão direito na pasta "Root",
    escolha o comando "Exportar..." e salve-o em seu disco rígido.

  - Para exportar (extrair) um único arquivo da pasta, clique com o botão direito sobre ele,
    escolha "Exportar" e salve-o em seu disco rígido.
    Você NÃO pode escolher mais de UM arquivo ou pasta por vez.
    A extração da pasta pode ser cancelada. Para cancelar, clique com o botão direito no campo "Estrutura"
    e escolha "Cancelar".

  - Para substituir (importar) um único arquivo, clique com o botão direito sobre ele,
    escolha "Importar..." e selecione o arquivo desejado em seu disco.
    Você NÃO pode importar uma pasta (ainda). Apenas um único arquivo pode ser substituído.

    // Você pode tentar importar arquivos um pouco maiores que os originais.
    // Se o GCR encontrar espaço suficiente entre o arquivo que você deseja substituir e um arquivo,
    // que segue na imagem, você pode fazer essa importação.

Para substituir arquivos ou pastas na imagem extraída, faça isso
no seu gerenciador de arquivos favorito como o Explorer, etc.
e ENTÃO carregue sua imagem extraída via Root->Open.

---------------------------------------------------------
Alguns conselhos úteis:
---------------------------------------------------------

- Arraste e solte uma imagem do GameCube ou uma pasta "Root" de uma imagem extraída do GameCube
   ao ícone de um programa e ele o abre no modo adequado
   (como "Root" ou como "Imagem"), dependendo do que você deseja abrir.

- Salve sua nova imagem reconstruída em outra unidade física diferente da sua "Root",
   se você quiser tornar as coisas mais rápidas.

- Para pausar/cancelar qualquer operação cancelável, basta pressionar ESC.

- Use a interface de linha de comando para automatizar seu trabalho.


*********************************************************************

Você pode encontrar as versões mais recentes do GCR nos seguintes sites:

- http://shedevr.org.ru/zelda64rus/downloads.html#romhacking_gc
(este site está em russo, mas você encontrará a ferramenta facilmente).
- http://www.romhacking.net/?page=utilities&platform=33&author=1147

*********************************************************************


---------------------------------------------------------
Graças a:
---------------------------------------------------------

- Nintendo por fazer jogos tão excelentes que nos fazem passar noites inteiras
   reproduzi-los e traduzi-los;

- Anton do "zelda64rus" pelo suporte e teste da ferramenta.


---------------------------------------------------------
Histórico de versões:
---------------------------------------------------------

Versão 1.1 - 19 de setembro de 2016
Suporte à interface de linha de comando.

Versão 1.0 - 12 de julho de 2009.
Primeiro lançamento público.


**************************** ISENÇÃO DE RESPONSABILIDADE ****************************

Este programa é gratuito. Foi escrito pela BSV e é fornecido como está.
Não há garantia de que funcionará e nenhuma garantia de que não causará nenhum dano.
Use este programa por sua conta e risco! Se você não concorda com isso - não use :)

Você NÃO pode vender este programa ou usá-lo de qualquer outra forma comercial.
Você NÃO pode modificar seu código de forma alguma.
Você NÃO pode distribuí-lo SEM este arquivo de texto.
Nesses casos, você DEVE perguntar primeiro ao autor (BSV - bsv798@gmail.com).




(c) 2016 BSV, Todos os direitos reservados.