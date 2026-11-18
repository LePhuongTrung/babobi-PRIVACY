# Política de privacidade — BabiBo

BabiBo é desenvolvido por Le Phuong Trung.

_Última atualização: 18 de novembro de 2026_

BabiBo é uma app de finanças pessoais para iPhone. Não é uma app para iPad.
Quem a publica não opera um serviço que receba o seu livro-razão. Não há conta
BabiBo, não há analítica, não há relatórios de falhas, não há identificador de
publicidade e não há um SDK de terceiros que envie dados por si.

Algumas funções enviam dados para fora do dispositivo, para uma empresa que
escolhe ou para um sítio que a função tem de alcançar. Esta página diz o que
sai, como, porquê, quem recebe (incluindo o fornecedor de IA), durante quanto
tempo fica guardado e como o pára ou apaga.

## O que fica no dispositivo

Tudo o que o livro-razão conhece — contas, saldos, movimentos, categorias,
orçamentos, posições, fotografias de recibos e nomes já aprendidos de um
recibo — fica num ficheiro de base de dados dentro do contentor da app no seu
dispositivo.

Esse ficheiro entra na cópia de segurança do dispositivo. Se o iCloud Backup
estiver ligado, uma cópia cifrada segue com o resto do telefone. Essa cópia é
entre si e a Apple. Nós não a conseguimos ler.

Pode exportar o ficheiro em qualquer momento em **Definições → Dados** e
importá-lo no BabiBo noutro dispositivo. Uma cópia restaurada não traz a
sessão do banco: a chave de assinatura fica no telefone que a criou, e volta a
ligar o banco no telefone novo.

Apagar a app apaga este ficheiro. Isso inclui uma chave de API Gemini guardada,
os nomes de produtos já aprendidos, os preços guardados e os logótipos em
cache.

Não usamos estes dados para publicidade nem rastreio, e nunca recebemos uma
cópia.

## O seu banco, através do Enable Banking

Opcional, no iPhone, no Mac e num servidor que aloje. Nada é enviado até
registar a sua própria aplicação no Enable Banking e ligar um banco.

**O quê.** Saldos, extratos (os movimentos) e os identificadores de conta que
o banco devolve, incluindo um IBAN quando o banco envia um.

**Como.** A app pergunta ao Enable Banking, que pergunta ao seu banco, e
escreve a resposta no ficheiro local. O identificador da aplicação e a chave
privada ficam no seu dispositivo. No iPhone, depois de um banco estar ligado,
a app pede ao iOS que a acorde de manhã — aponta para as 07:15 e salta a
transferência se uma sincronização já tiver tido êxito nas últimas seis horas
— e transfere de novo os extratos. O iOS pode ignorar essa hora. A
transferência só corre enquanto a atualização em segundo plano estiver ligada
para o BabiBo.

**Porquê.** Para encher o livro-razão. Se permitiu notificações, o telefone
também publica um resumo quando chegam movimentos novos. Essa notificação é
criada no dispositivo. Não nos é enviada.

**Quem.** Enable Banking e o seu banco. Não nós. O que fazem com os dados segue
os termos deles e o consentimento que dá ao registar-se e ao aprovar o banco.

**Durante quanto tempo, e como parar.** A cópia na app fica até apagar a
conta. Apagar uma conta apaga os movimentos dela e, quando é a última conta
dessa ligação, apaga a ligação, de modo que a transferência da manhã já não
tem nada para pedir. O Enable Banking e o banco guardam o que os seus termos
exigem. Nós não conseguimos apagar a cópia deles. Revogue o consentimento no
seu banco, ou na aplicação Enable Banking que registou.

## Google Gemini

Opcional, e só no iPhone. Não é feito nenhum pedido até guardar uma chave em
**Definições → Recibos de compra**.

**O quê.** Os nomes abreviados dos artigos impressos num recibo, e o nome da
loja. Não a fotografia, não os montantes, não as datas e não o resto do
livro-razão. Um pedido adicional pode enviar palavras de categoria já
guardadas no telefone — palavras como « frango », sem loja, montante ou data —
para as arquivar numa lista fixa de famílias de produtos.

**Como.** Cria uma chave em
[Google AI Studio](https://aistudio.google.com) e guarda-a nas Definições. A
app chama então a API Gemini da Google
(`generativelanguage.googleapis.com`) com essa chave. Um rótulo já respondido
uma vez fica no telefone e não volta a ser enviado.

**Porquê.** Para transformar uma abreviatura de caixa num nome de produto e
numa categoria, que são escritos de volta no ficheiro local.

**Quem.** A Google, segundo os termos da API Gemini que se aplicam à chave que
criou. Nós não recebemos o texto. A Google é o fornecedor de IA desta função.

**Durante quanto tempo, e como parar.** A Google guarda o que esses termos
dizem. Nós não fixamos esse prazo e não temos uma cópia num servidor nosso. A
leitura fica na base de dados local até apagar a app. **Definições → Recibos
de compra → Retirer** apaga a chave do telefone e pára os pedidos seguintes. O
botão chama-se Retirer. Não apaga leituras já guardadas no telefone, e não
apaga o que a Google já recebeu. Apague ou rode a chave também no Google AI
Studio se quiser que a Google deixe de a aceitar.

## Yahoo Finance

**O quê.** Um símbolo de cotação, como `CW8.PA`. Quando procura um título, o
texto que escreveu. Não a quantidade, não o valor e não o nome da conta.

**Como.**

- No iPhone, uma atualização do livro-razão pede à Yahoo um preço por cada
  posição que tenha um símbolo. Guardar um símbolo pergunta de imediato. O
  campo de pesquisa pergunta quando pesquisa. A app não o faz na transferência
  em segundo plano da manhã.
- No Mac, e num servidor que aloje, a Yahoo só é usada se puser o fornecedor
  de preços na Yahoo. A predefinição está desligada, e essas versões não fazem
  então nenhum pedido de cotação.

O pedido vai para `query1.finance.yahoo.com`. Não há chave de API. A ligação
também leva o endereço de rede e um user agent, como qualquer pedido HTTPS. A
app não acrescenta um nome nem um identificador de conta.

**Porquê.** Para mostrar um preço e, no iPhone, para encontrar a cotação que
corresponde ao que escreveu.

**Quem.** Yahoo. Não nós.

**Durante quanto tempo, e como parar.** Os preços são escritos no ficheiro
local e ficam até apagar a app. A Yahoo guarda os seus próprios registos
segundo a sua política de privacidade. Não temos uma conta Yahoo com que os
apagar. No iPhone, apague a posição para parar mais pedidos de preço sobre ela,
e não pesquise se não quiser que o texto seja enviado. No Mac e no seu
servidor, volte a pôr o fornecedor de preços em `none`.

## Sítios dos comerciantes

Só iPhone. Ligado por predefinição.

**O quê.** Nenhum campo do livro-razão é anexado ao pedido. A app carrega
`https://` mais o domínio do comerciante, e depois o ícone que essa página
nomeia. O pedido parece um navegador a pedir esse endereço: o próprio
endereço, o endereço de rede do telefone e um user agent de navegador. As
cookies não são guardadas nem enviadas.

**Como.** Enquanto **Definições → Categorias e comerciantes → Logótipos dos
comerciantes** estiver ligado, e um comerciante tiver um sítio conhecido ou um
sítio que escreveu. A imagem é pedida na primeira vez em que é precisa.

**Porquê.** Para desenhar o ícone desse comerciante. Mais nada.

**Quem.** O sítio desse comerciante, e quem o aloja. Não um serviço de
logótipos, e não nós.

**Durante quanto tempo, e como parar.** A imagem fica na cache da app até o
iOS limpar as caches ou apagar a app. Um sítio sem um ícone utilizável não
volta a ser pedido durante sete dias. Os registos do sítio são dele; nós não
os conseguimos apagar. Desligue **Logótipos dos comerciantes** para parar
pedidos novos.

## Um servidor seu

Opcional. Se apontar o BabiBo para um servidor que opere, a app lê e escreve
ali o livro-razão. Essa máquina é sua. Retire o endereço do servidor nas
Definições para parar. Apague o que o servidor guardou nessa máquina.

## Face ID

Se ligar o bloqueio da app, o BabiBo pede ao iOS que o verifique. O iOS
responde sim ou não. Os seus dados biométricos nunca chegam à app, e não são
enviados a ninguém.

## Crianças

O BabiBo não se dirige a crianças.

## Alterações

Qualquer alteração desta política fica registada em
<https://github.com/LePhuongTrung/babobi-PRIVACY>, onde o histórico é público.

Esta página está em português. A mesma política em inglês é PRIVACY.md na
raiz. As outras línguas da app estão numa pasta com o código da língua.

## Contacto

Não há uma conta BabiBo para apagar, porque não guardamos nenhuma. Apagar a
app apaga o ficheiro local. Para dados que um destinatário já tenha, use o
caminho indicado na secção desse destinatário.

Perguntas: <babibo.support@lephuongtrung.id.vn>
