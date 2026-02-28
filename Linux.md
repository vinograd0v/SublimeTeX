Para esta guía voy a suponer que tienes un conocimiento decente de linux, de todas maneras, al ser un tema sencillo la IA puede ayudar. Primero, aclaro que esta guía es para mi setup actual: Archlinux-Hyprland, si vienes de distribuciones basadas en debian u otras, probablemente estas instrucciones son totalmente usables, pero aclaro que pueden cambiar un poco.

La guía para linux es bastante más rápida que la de windows, no lidiamos con el problema del path, en cambio solo debemos instalar las dependencias, texlive, zathura y sublimetext. Posteriormente, una vez instaladas las apps, podemos volver a las instrucciones de windows y configurar SublimeText exactamente igual que como se hace en windows, la única diferencia es que la carpeta donde se alojan los archivos de configuración de SublimeText tiene una ruta distinta, sin embargo se puede ingresar a ella de la misma forma explicada allí o buscandola manualmente.

Primero instalamos TexLive.

```
sudo pacman -S texlive
```

Ahora instalamos SublimeText, esto, nuevamente es para Archlinux, en la página de SublimeTex probablemente encuentres cómo instalarlo en tu distro.

```
curl -O https://download.sublimetext.com/sublimehq-pub.gpg && sudo pacman-key --add sublimehq-pub.gpg && sudo pacman-key --lsign-key 8A8F901A && rm sublimehq-pub.gpg
```

```
echo -e "\n[sublime-text]\nServer = https://download.sublimetext.com/arch/stable/x86_64" | sudo tee -a /etc/pacman.conf
```

```
sudo pacman -Syu sublime-text
```

Ahora necesitamos instalar zathura, biber, etc.

```
sudo pacman -S zathura zathura-djvu zathura-pdf-poppler biber texlive-langspanish python-dbus
```

Una vez hecho esto abrimos SubliText y continuamos con la configuración desde la parte "Sublime Configs"

## Resultado final

![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/image.png)