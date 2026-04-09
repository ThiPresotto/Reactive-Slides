# Projeto de conclusao de curso

Aurora é uma engine escrita na linguagem Atmos que processa apresentações definidas através de tabelas Lua. Para criar uma apresentação, execute o seguinte comando no terminal: `atmos aurora presentation`. O arquivo presentation deve ser um array de slides — ou seja, uma de tabela de tabelas na linguagem Lua — onde cada tabela contém informações específicas referente de um slide.

Abaixo está um exemplo de como deve ser estruturado um arquivo presentation:

```
return {
        --Primeiro Slide
        {
                template = "FrontCover",
                bgcolor = "white",
                titlestr = "Quine Program",
                autorstr = "Peterson Marry",
                unistr = "Universidade do Estado do Rio de Janeiro",
                datestr = "20/10/1984",
        },
        --Segundo Slide
        {
                template = "Slide_Title_OneObject",
                bgcolor = "white",
                title = "Caracteristicas Necessarias",
                {
                        tag = "BulletList",
                        "Caracteristicas Necessarias",
                        "Sem programas vazios/sem byte",
                        "Sem usar leitura de arquivos para ler a si mesmo",
                        "A saída precisa ser idêntica ao código fonte."
                },
    },
    --Terceiro Slide
   {
        template = "Slide_Title_OneObject",
        bgcolor = "white",
        title = "Código em C",
        {
            tag = "Text",
            [[#include <studio.h>
int main(){
char*s=#include <studio.h>%cint main(){char*s=%c%s%c;printf(s,10,34,s,34);return 0;}
printf(s,10,34,s,34);return 0;}]],
        } 
    }
}
```
O exemplo acima irá renderizar uma apresentação com três slides.


Todo slide possui o campo template como obrigatório. O campo bgcolor é opcional — quando omitido, a Aurora aplica branco como cor padrão. Os templates disponíveis são:

## FrontCover
Slide de capa. Ele irá apresentar as informações de forma padronizada. Os campos que esse template aceita são: 
titlestr (título da apresentação), 
substr (subtítulo da apresentação),
autorstr (nome do autor), 
unistr (instituição)
datestr (data no formato string).

## Slide_Title_OneObject
Slide com título e um único objeto de conteúdo.
Os objetos podem ser um texto, uma imagem ou uma lista bullet (Explicação sobre cada objeto adiante). 
Abaixo segue um exemplo de slide com este template:

```
{
        template = "Slide_Title_OneObject",
        bgcolor = "white",
        title = "Código em C",
        {
            tag = "Text",
            [[#include <studio.h>
int main(){
char*s=#include <studio.h>%cint main(){char*s=%c%s%c;printf(s,10,34,s,34);return 0;}
printf(s,10,34,s,34);return 0;}]],
        } 
    }
```
template = Formato padrão do slide
bgcolor = Cor de fundo
title = Título do frame atual
objeto = Tabela sem nome, neste exemplo representa um objeto de texto.


## Slide_Title_TwoObjects
Slide com título e dois objetos de conteúdo lado a lado. Os objetos podem ser um texto, uma imagem ou uma lista bullet (Explicação sobre cada objeto adiante). Abaixo um exemplo de slide neste template:

```
{
        template = "Slide_Title_TwoObjects",
        bgcolor = "white",
        title = "boba",
        {
            tag = "BulletList",
            "Anos dos títulos",
            "1974",
            "1989",
            "1997",
            "2001"
        },
        {
            tag = "BulletList",
            "Anos dos titulos",
            "1970",
            "1984",
            "2010",
            "2012"
        }
    }
```
template = Formato padrão do slide
bgcolor = Cor de fundo
title = Título do frame atual
objeto = Tabela sem nome, no template 'Slide_Title_TwoObjects haverá duas tabelas, cada um representando um objeto distinto.

## Objetos de Conteúdo

Conforme mencionado nos templates há alguns objetos que podem ser adicionados. Os objetos são tabelas anônimas que representam o conteúdo do slide. Todo objeto deve conter o campo tag, que indica seu tipo. A engine reconhece três tipos de objetos: Text, Image e BulletList.

### Text

Objeto utilizado para exibir blocos de texto. O conteúdo deve ser inserido no primeiro campo anônimo da tabela como uma string (podendo ser multilinha com [[ ]]). A engine aplica posicionamento padrão conforme o template, mas os seguintes campos opcionais permitem personalização:

`text_clr`-> Altera a cor do texto, deve ser um valor da tabela "colors" ou um número em hexadecimal.

`text_size`-> Altera o tamanho da fonte, deve ser um valor da tabela "sizes.text" ou um número decimal.

`text_xstart`-> Altera a posição inicial do texto no eixo x, deve ser um decimal positivo.

`text_ystart`-> Altera a posição inicial do texto no eixo y, deve ser um decimal positivo.

### Image

Objeto utilizado para inserir imagens. No primeiro campo anônimo da tabela, o path da imagem deve ser inserido. A engine aplica posicionamente padrão conforme o template, mas os seguintes campos opcionais permitem personalização:

`image_pos` -> Altera o ponto de âncora do centro da imagem. Deve ser um valor da tabela "fs".

`image_scale` -> Altera o tamanho mantendo sua razão. Deve ser um valor da tabela "sizes.image" ou um número decimal.

`image_xshift` -> Movimenta a imagem pelo eixo x, somando esse valor, definido como 0 por padrão tendo o ponto de ancoragem como referência.

`image_yshift` -> Movimenta a imagem pelo eixo y, somando esse valor, definido como 0 por padrão tendo o ponto de ancoragem como referência.

### BulletList

Objeto utilizado para inserir informações como uma lista não ordenada. Cada campo anônimo da tabela desse objeto é uma string que será adicionada a um tópico. A engine aplica posicionamente padrão conforme o template, mas os seguintes campos opcionais permitem personalização:

`bullet_xstart`-> Altera a posição inicial do texto no eixo x, deve ser um decimal positivo.

`bullet_ystart`-> Altera a posição inicial do texto no eixo y, deve ser um decimal positivo.

## Tabelas

Como visto anteriormente, alguns valores são pré-estabelecidos em tabelas auxiliares, como as cores na tabela colors e os tamanhos de fonte na tabela sizes. Abaixo seguem as informações disponíveis em cada tabela:

### colors

```
{

black .. 0x000000,
white .. 0xFFFFFF,
red .. 0xFF0000,
green .. 0x00FF00,
blue .. 0x0000FF,
yellow .. 0xFFFF00,
cyan .. 0x00FFFF,
magenta .. 0xFF00FF

}
```
### sizes.text

```
{
tiny = 15,
small = 25,      
normal = 45, 
large = 60,   
giant = 80,
}
```

### sizes.image

```
{
tiny = 100,
small = 150,
normal = 300,
large = 500,
giant = 750,
}
```

### fs

```
{
C .. Centro
L .. Leste
O .. Oeste
N .. Norte
S .. Sul
SL .. Sudeste
SO .. Sudoeste
NO .. Noroeste
NL .. Nordeste
}
```