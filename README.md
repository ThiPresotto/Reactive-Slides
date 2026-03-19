# Projeto de conclusao de curso



func BackgroundColor(t)
-->Define a cor de fundo do slide
```
@{
        ;;Esse slide pode receber também uma imagem?
        clr_value       .. cor do plano de fundo, precisa ser uma chave da
                             tabela colors.
}
```
---

func Image(t) 
--> template para inserir imagens, campos da tabela t...
```
@{
        path         .. caminho da imagem.
        anchorSlide  .. posição da imagem no slide, precisa ser uma chave da tabela "fs". 
        anchorImg    .. ponto de referência da imagem a ser ancorada, precisa ser uma chave da tabela "fs".          
        scale        .. operação de escala na imagem, precisa ser uma chave da tabela "sizes"
}
```
---

func Text(t)
-->Bloco de texto que será inserido no slide, campos da tabela t...
```
@{
        string             .. texto a ser inserido.
        font_size          .. tamanho do texto, precisa ser uma chave da tabela "sizes".
        text_clr::string    .. cor do texto, precisa ser chave da tabela "colors".
}
```
---

func BulletList(t)
--> Informação apresentada como lista não ordenada, campos da tabela t...
```
@{
        items           .. tabela/array com strings, cada item será apresentado como um tópico do bullet.
        anim            .. true  -> os bullets são apresentados um a um através das setas Up e Down
                           false -> as informações são apresentadas diretamente na tela
}
```
---

func Slide_Front(t)
--> Template para capa da apresentação, a tabela t aceita os seguintes campos...
```

@{
        todos os campos são opcionais
        title              .. titulo da apresentação, apresentado no topo da página
        subtitle           .. subtítulo, apresentado logo abaixo do título.
        author             .. nome do autor, apresentado no centro
        institute          .. instituição de ensino da apresentação
        date               .. data da apresentação
}
```
---

func Slide_Title-OneObject(t)
--> Template para slide com título e informação, a tabela t aceita os seguintes campos...
```

@{
        todos os campos são opcionais
        title              .. titulo do slide atual, apresentado no topo da página
        object1              .. informação apresentada no slide.
}
```
---

func Slide_Title-TwoObjects(t)
--> Template para slide com título e informação posta lado a lado, a tabela t aceita os seguintes campos...
```

@{
        todos os campos são opcionais
        title              .. titulo do slide atual, apresentado no topo da página
        data1              .. informação apresentada no slide na coluna da esquerda. @{tag,conteudo}
        data2              .. informação apresentada no slide na coluna da direita.
}
```
---

func Slide_InfoOverInfo(t)
--> Template para slide com título e texto acima de uma imagem. 

```

@{
        todos os campos são opcionais
        title              .. titulo do slide atual, apresentado no topo da página
        info1              .. informação apresentada acima de info 2
        info2              .. informação apresentada abaixo de info 1
}
```
---

func Slide_InfoOverImages(t)
--> Template para slide com título e texto acima de uma imagem. 

```

@{
        todos os campos são opcionais
        title              .. titulo do slide atual, apresentado no topo da página
        info1              .. informação apresentada acima de info 2
        images             .. tabela com 1 a 4 campos com paths para imagens.
}
```
---

slides.fs

--> Tabela com posição do objeto em relação à janela

```

@{

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

---  

slides.BackgroundColor

--> Tabela de cores de fundo

```

@{

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
---

slides.sizes

--> Tabela com os tamanhos para imagens e texto. Ordenados do menor ao maior...
@{
        tiny
        small      
        medium  
        normal   
        large       
        giant
}