---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: eedba16136ad394bda45cc871944f9b876c8ee38
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opções de ferramentas de desenvolvimento: IDE ou editor

Não importa se você preferir um IDE avançado e completo ou um editor de leve e ágeis, a Microsoft tem você quando se trata de desenvolvimento de aplicativos do Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)

Se você preferir um editor leve, de plataforma cruzada com suporte a qualquer linguagem de desenvolvimento, você pode usar o código do Visual Studio e a CLI do Docker. Esses produtos oferecem uma experiência simple e sólida, que é essencial para simplificar o fluxo de trabalho do desenvolvedor. Ao instalar o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores de Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução). Além disso, o código do Visual Studio oferece suporte a extensões de Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar os comandos do editor.

> [!NOTE]
> Para baixar o código do Visual Studio, vá para <https://code.visualstudio.com/download>.

Para baixar o Docker para Mac e Windows, vá para <http://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio com ferramentas do Docker

Quando você estiver usando o Visual Studio 2015, você pode instalar as ferramentas de complemento "Docker Tools para Visual Studio". Para o Visual Studio de 2017, ferramentas do Docker vir internas já. Em ambos os casos, você pode desenvolver, executar e validar seus aplicativos diretamente no ambiente de Docker escolhido. F5 seu aplicativo (contêiner único ou vários contêineres) diretamente em um Docker host com a depuração, ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner. Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows Criando contêineres do Docker para Windows ou do Linux.

> [!NOTE]
> Para baixar as ferramentas do Docker para o Visual Studio, vá para <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Opções de idioma e do framework

Você pode desenvolver aplicativos do Docker e ferramentas da Microsoft com as linguagens mais modernas. A seguir está uma lista inicial, mas não se limitam a ela:

-   .NET core e ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

Basicamente, você pode usar qualquer linguagem moderna com suporte pelo Docker no Windows ou do Linux.


>[!div class="step-by-step"]
[Anterior] (orquestrar-alta-escalabilidade-availability.md) [Avançar] (docker-aplicativos-interna-loop-workflow.md)
