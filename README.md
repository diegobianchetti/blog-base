***O que otimizei no blog até agora e o que estou utilizando para manter o conteúdo***

**Importante para o GitHub**

```
2019-02-08 19:59:21 ⌚  tortuga in ~/Workspace/TortugaVoladora/tortugavoladora.life
± |master ✓| → git remote -v
origin	git@github.com:diegobianchetti/blog-base.git (fetch)
origin	git@github.com:diegobianchetti/blog-base.git (push)

2019-02-08 19:59:33 ⌚  tortuga in ~/Workspace/TortugaVoladora/tortugavoladora.life
± |master ✓| → cd _site/

2019-02-08 19:59:37 ⌚  tortuga in ~/Workspace/TortugaVoladora/tortugavoladora.life/_site
± |master ✓| → git remote -v
origin	git@github.com:diegobianchetti/tortugavoladora.life.git (fetch)
origin	git@github.com:diegobianchetti/tortugavoladora.life.git (push)
```

- Jekyll para criar o blog com conteúdo estático. (https://jekyllrb.com/)
O tema que estou utilizando é Trophy-Jekyll (https://github.com/thomasvaeth/trophy-jekyll)

- Tudo está armazenado e utilizando o servico HTTP do GitHub. (https://github.com)
As imagens são armazenadas no Flickr e são exibidas no blog por links. (https://www.flickr.com/)

- Imagens nos posts devem ter as seguintes configuracões:

  - image: large 1600x1200 - imagem que aparece do lado esquerdo é a mesma imagem principal do post
  - image-sm: medium 500x375 - imagem que aparece nas categorias

- **Criar galeria de imagem**

Para galeria estática - no cabecalho do post definir:
```
gallery:
  - link imagem 1
  - link imagem 1
  - link imagem N
```
Para apresentar a galeria do corpo do post é só dar um include na galeria de imagens com o código abaixo:
```
{% include gallery.html %}
```
É possivel adionar uma galeria de imagens estática adicional:
```
gallery2:
  - link imagem 1
  - link imagem 1
  - link imagem N
```
Para apresentar a galeria do corpo do post é só dar um include na galeria de imagens com o código abaixo:
```
{% include gallery2.html %}
```


Para galeria com SWIPE - no cabecalho do post definir:
```
swipe_gallery:
  - link imagem 1
  - link imagem 1
  - link imagem N
```
Para apresentar a galeria do corpo do post é só dar um include na galeria de imagens com o código abaixo:
```
{% include swipe-gallery.html %}
```


- **Inclusão de video do youtube**

Referência: https://adam.garrett-harris.com/how-to-easily-embed-youtube-videos-in-jekyll-sites-without-a-plugin/

Na posicão do post que quero o video só preciso dar um include no player com o código abaixo:
```
{% include youtubePlayer.html id="kx1U53N3nY0" %}
```

- **Adicionando comentários aos posts**
  - https://blog.webjeda.com/jekyll-comments/
  - criei o arquivo `_includes/disqus.html`
  - no `_layouts/post.html` difine o local de insercão dos comentários em todos os posts declarando `{% include disqus.html %}`

**Descricão de Pojeto**
- Para adicionar uma descricão de projeto é necessário criar um arquivo no diretório `_includes` no mesmo formado do arquivo nordesde2017.html. Esse arquivo deve armazenar o texto e demais elementos que serão utilizados na apresentacão do projeto e esse texto será importado pelo layout 'category_index.html'.


**Sobre**
- Menu "Sobre" possui uma configuracão a parte, me baseie na estrutura do archive para criar esse item no menu e linkar com o conteúdo que está no html separado.
     - no diretorio `_includes` criei o arquivo about-link.html que cria o link e aponta para <sitel.url>/about/
     - na raiz do site criei o about.hmtl (pode ser outro nome) e no cabecalho de configuracão desse aquivo defini permalink: /about/


Toda estrutura do blog está no diretório base do tema ~/Workspace/TortugaVoladora/tortugavoladora.life. O conteúdo desse diretório é toda a estrutura do site. Baixando o repositório dele é possível compilar site do zero e gerar o conteúdo completo.

Reporitório BLOG-BASE (https://github.com/diegobianchetti/blog-base)

```
cd Workspace/TortugaVoladora/tortugavoladora.life/
git add . (gad)
git status (gst)
git commit -m "descricão da alteracão" (gc -m "")
git push origin master (gpo master)
```

executar jekyll:
```
bundle exec jekyll b (build)
bundle exec jekyll s (server)
```

O site compilado fica no diretório `_site` dentro da base do tema. O conteúdo desse diretório mais o arquivo CNAME são enviados para o GitHub-Pages e é o conteúdo estático do site.

Repositório BLOG (https://github.com/diegobianchetti/tortugavoladora.life)

```
cd _site/
git add . (gad)
git status (gst)
git commit -m "descricão da alteracão" (gc -m "")
git push origin master (gpo master)
```

- **Atualizando repositórios**
O script build-and-update-commit.sh executa os comando necessários para o gerar o conteúdo estático através do build e envia as alteracões locais para os repositórios, tanto do site estático quanto do conteúdo gerador do site estático, servindo assim como um backup geral.

```
 2018-05-05 22:26:02 ⌚  tortuga in ~/Workspace/TortugaVoladora/tortugavoladora.life
± |master ✓| → sh build-and-update-commit.sh

Usage: sh build-and-update-commit.sh "commint message"
 ```

- **O Analytics foi adicionado ao blog seguindo esse toturial**
https://michaelsoolee.com/google-analytics-jekyll/



- **Solucão de alguns problemas que estava tendo com Jekyll na geracão do site depois de muito tempo sem atualizar ambos, o site e o sistema**
```
gem update
bundle update jekyll
```
