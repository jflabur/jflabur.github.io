---
title: Cómo configurar un buen entorno de trabajo en Linux
layout: single
excerpt: Para aquellos interesados en certificarse de OSCP, por aquí os dejo una guía
  hecha por mi donde de manera desglosada comentamos cada uno de los puntos importantes
  a tener en cuenta de cara a la examinación.
date: '2020-09-26 01:00:00'
classes: wide
header:
  teaser: "/assets/images/oscp-preparation/oscp-logo.png"
  teaser_home_page: true
categories:
- Certificaciones
tags:
- OSCP
- Offensive Security
- Pentesting
- Examen
- Guías
---

## Índice y Estructura Principal
   
- [Introduccion](#introduccion)
- [Instalando bspwm](#instalando-bspwm)
- [Instalando dependencias de bspwm](#instalando-dependencias-de-bspwm)
- [Instalando sxhkd](#instalando-sxhkd)
- [Fijando archivos de configuracion para los servicios sxhkd y bspwm](#fijando-archivos-de-configuracion-para-los-servicios-sxhkd-y-bspwm)
- [Configurando archivo ~/.xinitrc](#configurando-archivo-xinitrc)
- [Instalando compton](#instalando-compton)
- [Creando configuracion para el manejo sobre aplicaciones Java](#creando-configuracion-para-el-manejo-sobre-aplicaciones-java)
- [Instalando feh](#instalando-feh)
- [Configurando el prefix a mod1 (Tecla Windows)](#configurando-el-prefix-a-mod1-tecla-windows)
- [Configurando fichero sxhkdrc](#configurando-fichero-sxhkdrc)
- [Instalando Rofi](#instalando-rofi)
- [Configurando utilidad de resize para el sxhkd (Creando script personalizado)](#configurando-utilidad-de-resize-para-el-sxhkd-creando-script-personalizado)
- [Entrando a bspwm con la configuracion establecida](#entrando-a-bspwm-con-la-configuracion-establecida)
- [Sincronizando compton con bspwm](#sincronizando-compton-con-bspwm)
- [Creando fichero de configuracion para compton](#creando-fichero-de-configuracion-para-compton)
- [Ajustando transparencia para algunos servicios](#ajustando-transparencia-para-algunos-servicios)
- [Configurando floating window para el servicio deseado](#configurando-floating-window-para-el-servicio-deseado)
- [Configurando fondo de escritorio](#configurando-fondo-de-escritorio)
- [Creando efecto blur al fondo con compton](#creando-efecto-blur-al-fondo-con-compton)
- [Configurando Polybar](#configurando-polybar)
- [Creando launcher en Bash para Polybar](#creando-launcher-en-bash-para-polybar)
- [Sincronizando Polybar con Bspwm](#sincronizando-polybar-con-bspwm)
- [Reinstalando Polybar con la version 3.4.0 (La otra da problemas)](#reinstalando-polybar-con-la-version-340-la-otra-da-problemas)
- [Instalando fuente de Hacker Nerd Fonts](#instalando-fuente-de-hacker-nerd-fonts)
- [Lanzando Polybar](#lanzando-polybar)
- [Configurando fuente](#configurando-fuente)
- [Configurando la Polybar](#configurando-la-polybar)
- [Sincronizando fuente Hacker Nerd Fonts en la Polybar](#sincronizando-fuente-hacker-nerd-fonts-en-la-polybar)
- [Creando nuestros propios modulos para la Polybar](#creando-nuestros-propios-modulos-para-la-polybar)
- [Configurando utilidad de HackTheBox en la Polybar](#configurando-utilidad-de-hackthebox-en-la-polybar)
- [Probando configuracion de la Polybar](#probando-configuracion-de-la-polybar)
- [Configurando transparencia de la Polybar](#configurando-transparencia-de-la-polybar)
- [Instalando Powerlevel10k y configurando consola ZSH](#instalando-powerlevel10k-y-configurando-consola-zsh)
- [Personalizando la Powerlevel10k](#personalizando-la-powerlevel10k)
- [Configurando nuestros propios iconos en la Powerlevel10k](#configurando-nuestros-propios-iconos-en-la-powerlevel10k)
- [Cambiando el tipo de terminal para los usuarios existentes a nivel de sistema](#cambiando-el-tipo-de-terminal-para-los-usuarios-existentes-a-nivel-de-sistema)
- [Creando enlace simbolico para el fichero .zshrc del usuario root](#creando-enlace-simbolico-para-el-fichero-zshrc-del-usuario-root)
- [Configurando el fichero .zshrc](#configurando-el-fichero-zshrc)
- [Instalando lsd (ls con esteroides)](#instalando-lsd-ls-con-esteroides)
- [Centralizando en el .zshrc aliases para lsd](#centralizando-en-el-zshrc-aliases-para-lsd)
- [Configurando utilidad 'bat' (cat con esteroides)](#configurando-utilidad-bat-cat-con-esteroides)
- [Configurando man](#configurando-man)
- [Instalando fzf para zsh](#instalando-fzf-para-zsh)
- [Creando funcion personalizada para fzf en zsh](#creando-funcion-personalizada-para-fzf-en-zsh)
- [Instalando Plugins en ZSH](#instalando-plugins-en-zsh)
- [Instalando i3lock-fancy y imagemagick para el bloqueo de pantalla](#instalando-i3lock-fancy-y-imagemagick-para-el-bloqueo-de-pantalla)
- [Lanzar proceso con sxhkd bajo un contexto privilegiado](#lanzar-proceso-con-sxhkd-bajo-un-contexto-privilegiado)


Introduccion
===============================================================================================================================
Antes que nada, me gustaría comentar una serie de puntos para aquellos que pretenden seguir esta guía.

## Instalando bspwm
xxxxxxxxxxxxxxxxxxxxxxxx

## Instalando dependencias de bspwm
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


<p align="center">
     <img src="https://funkyimg.com/i/346F1.png">
</p><br>

## Instalando sxhkd
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

##  Fijando archivos de configuracion para los servicios sxhkd y bspwm
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

## Configurando archivo ~/.xinitrc
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

##  Instalando compton
xxxxxxxxxxxxxxxxxxxxxx

##  Creando configuracion para el manejo sobre aplicaciones Java
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando feh
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando el prefix a mod1 (Tecla Windows)
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando fichero sxhkdrc
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando Rofi
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando utilidad de resize para el sxhkd (Creando script personalizado)
xxxxxxxxxxxxxxxxxxxxxx

##  Entrando a bspwm con la configuracion establecida
xxxxxxxxxxxxxxxxxxxxxx

##  Sincronizando compton con bspwm
xxxxxxxxxxxxxxxxxxxxxx

##  Creando fichero de configuracion para compton
xxxxxxxxxxxxxxxxxxxxxx

##  Ajustando transparencia para algunos servicios
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando floating window para el servicio deseado
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando fondo de escritorio
xxxxxxxxxxxxxxxxxxxxxx

##  Creando efecto blur al fondo con compton
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Creando launcher en Bash para Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Sincronizando Polybar con Bspwm
xxxxxxxxxxxxxxxxxxxxxx

##  Reinstalando Polybar con la version 3.4.0 (La otra da problemas)
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando fuente de Hacker Nerd Fonts
xxxxxxxxxxxxxxxxxxxxxx

##  Lanzando Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando fuente
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Sincronizando fuente Hacker Nerd Fonts en la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Creando nuestros propios modulos para la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando utilidad de HackTheBox en la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Probando configuracion de la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando transparencia de la Polybar
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando Powerlevel10k y configurando consola ZSH
xxxxxxxxxxxxxxxxxxxxxx

##  Personalizando la Powerlevel10k
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando nuestros propios iconos en la Powerlevel10k
xxxxxxxxxxxxxxxxxxxxxx

##  Cambiando el tipo de terminal para los usuarios existentes a nivel de sistema
xxxxxxxxxxxxxxxxxxxxxx

##  Creando enlace simbolico para el fichero .zshrc del usuario root
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando el fichero .zshrc
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando lsd (ls con esteroides)
xxxxxxxxxxxxxxxxxxxxxx

##  Centralizando en el .zshrc aliases para lsd
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando utilidad 'bat' (cat con esteroides)
xxxxxxxxxxxxxxxxxxxxxx

##  Configurando man
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando fzf para zsh
xxxxxxxxxxxxxxxxxxxxxx

##  Creando funcion personalizada para fzf en zsh
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando Plugins en ZSH
xxxxxxxxxxxxxxxxxxxxxx

##  Instalando i3lock-fancy y imagemagick para el bloqueo de pantalla
xxxxxxxxxxxxxxxxxxxxxx

##  Lanzar proceso con sxhkd bajo un contexto privilegiado
xxxxxxxxxxxxxxxxxxxxxx




¡Un saludo y que os sea leve!
