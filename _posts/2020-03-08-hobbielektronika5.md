---
title: Hobbielektronika - Mikrokontroller bootloader (Témázgató)
layout: post
author: montyx
categories: electronics
tags: hobbielekronika elektronika bootloader mcu
---
A Témázgató mindig egy kis rövid tartalom lesz, ha meg akarok osztani valami olyasmit, amit egy hosszabb lélegzetű posztban nem akartam kifejteni. Mivel az ITban az angol az alapnyelv, így nem igazán tudok a bootloaderre jó magyar kifejezést. Talán előtöltőnek tudnám nevezni. Biztos van rá valami okosság, de jobb bootloaderként megtanulni, és így használni.
Miről is van szó? Ha az ember megvesz mondjuk egy kínai klón arduinot, akkor az a meglepetés érheti, hogy nem mindig van rajta booloader. Amikor újraindul a board, nem villan fel a beépített LED rajta.

#### De mi is az a bootloader, és mire jó?
Nem más, mint egy olyan kis firmware rész, ami arról gondoskodik, hogy ne kelljen külső programozási eszközt használni az MCU firmware lecseréléséhez. Esetünkben az Arduinora írt kód a firmware nagyon leegyszerűsítve. Amikor megírod a kódot, és van bootloader "égetve" (burn bootloader) a flash memória területre, akkor az általad írt firmware kezelését a bootloader mini firmware részlete fogja kezelni. A bootloader gondoskodik az általad írt kód betöltéséről.
A bootloaderről tudni kell, hogy a program memóriából foglal el egy kis területet.

Ennyi lett volna ez a témázgató, majd később ki fogom vesézni bővebben is a bootloader témakörét. Ez csak azért született, hogy ha legközelebb leírom a bootloader szót, akkor tudd hova tenni.
De addig is a legjobbakat, jó kísérletezést, és sose add fel!
