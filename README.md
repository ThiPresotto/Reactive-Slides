# Projeto de conclusao de curso



slides.BackgroundColor
-->Define a cor de fundo do slide
```
@{
        clr_value::string .. cor do plano de fundo, precisa ser uma chave da
                             tabela colors.
}
```
---

slides.Image 
--> Insere uma imagem no slide
```
@{
        path::string .. caminho da imagem.
        pos::string  .. posição da imagem no slide, precisa ser uma chave da
                        tabela "fs". 
}
```
---

slides.Text
-->Bloco de texto que será inserido no slide.
```
@{
        string::string     .. texto a ser inserido.
        font_size::number  .. tamanho do texto.
        str_clr::string    .. cor do texto, precisa ser chave da tabela colors.
        x_start::number    .. posição de inicio no eixo x.
        y_start::number    .. posição de inicio no eixo y.
}
```
---

slides.FrontCover
--> Template para capa da apresentação
```
@{
        titlestr::string  .. titulo da apresentação
        autrostr::string  .. nome do autor
        unistr::string    .. instituição de ensino da apresentação
        datestr::string   .. data da apresentação
}
```
---

slides.BulletList
--> Informação apresentada como lista não ordenada
```
@{
        string::string  .. texto a ser inserido nos bullets, separado por quebra de linha (string                                  multilinha)
        anim::bool      .. true  -> os bullets são apresentados um a um através das setas Up e Down
                           false -> as informações são apresentadas diretamente na tela
}
```
