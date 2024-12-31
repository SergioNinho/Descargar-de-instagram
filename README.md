# Descargar-de-instagram
Proyecto Instagram Reel Downloader Este proyecto permite descargar reels de Instagram utilizando instaloader y requests.
## Requisitos
Python 3.7+

## Bibliotecas:

instaloader

requests

os

pathlib

## Instalación
Clona este repositorio.

Instala las bibliotecas necesarias utilizando pip:
```
pip install instaloader requests
```
## Uso
Para descargar reels de Instagram, puedes utilizar la función bajar_insta.

## Ejemplo de uso
```
import instaloader
import requests
import os
from pathlib import Path

def bajar_insta(link):
    # Crear una instancia de Instaloader
    L = instaloader.Instaloader()

    # URL del reel de Instagram
    reel_url = link

    # Obtener el post usando el shortcode
    post = instaloader.Post.from_shortcode(L.context, reel_url.split("/")[-2])
    titulo = post.title
    page_name = post.owner_username
    nombre ='Asurgir-' + page_name +'-' + titulo 
    # Extraer el URL del video MP4
    video_url = post.video_url

    # crear ruta
    path_insta = 'Videos'
    folder_insta = '@surgir.mp4'
    url_descargas_insta = str(Path.home() / path_insta)
    os.makedirs(url_descargas_insta +'/'+folder_insta, exist_ok=True)

    # Descargar el video MP4
    response = requests.get(video_url)
    with open(os.path.join(url_descargas_insta, folder_insta, nombre +".mp4"), "wb") as file:
        file.write(response.content)

    print("Descarga completada.")
    print(page_name)

# Ejemplo de llamada a la función
# bajar_insta('https://www.instagram.com/reel/DCfOQ3GxVfW/?utm_source=ig_web_copy_link')
```
## Contribución
Si deseas contribuir a este proyecto, por favor crea un fork del repositorio y abre un Pull Request con tus cambios.

## Licencia
Este proyecto está bajo la licencia MIT.
