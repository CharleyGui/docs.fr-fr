---
title: Outil d’installation de .NET pour les auteurs d’extensions VS Code
description: Vue d’ensemble de l’outil d’installation de .NET pour les auteurs d’extensions, une extension de Visual Studio Code pour l’installation du Runtime .NET.
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: 37be1b9dcdb9fba99554800fea23f28443efb5fa
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599913"
---
# <a name="net-install-tool-for-extension-authors"></a>Outil d’installation .NET pour les auteurs d’extensions

L' [outil d’installation de .net pour les auteurs d’extensions](https://github.com/dotnet/vscode-dotnet-runtime) est une extension de Visual Studio code qui permet d’acquérir le Runtime .net spécifiquement pour les auteurs d’extensions vs code. Cet outil est conçu pour être utilisé dans les extensions écrites en .NET et nécessiter .NET pour démarrer des éléments de l’extension (par exemple, un serveur de langage). L’extension n’est pas destinée à être utilisée directement par les utilisateurs pour installer .NET en vue du développement.

## <a name="getting-started-extension-authors"></a>Prise en main : auteurs d’extensions

Pour vous assurer que l’outil d’installation de .NET pour les auteurs d’extensions est adapté à votre scénario, commencez par examiner les [objectifs de cette extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) sur notre page github.

> [!NOTE]
> Cet outil peut être utilisé pour installer uniquement le Runtime .NET, mais il n’a actuellement pas la possibilité d’installer le kit de développement logiciel (SDK) .NET.

Une fois que vous avez vérifié que l’outil d’installation de .NET pour les auteurs d’extensions répond à vos besoins, vous pouvez en dépendre dans votre [manifeste d’extension](https://code.visualstudio.com/api/references/extension-manifest) et commencer à utiliser les commandes exposées avec l' [API vs code](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command). Vous pouvez trouver la liste des commandes exposées par cette extension sur notre [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).

Consultez cet [exemple d’extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) pour voir ces étapes en action.

Pour obtenir plus d’exemples, consultez ces extensions open source qui exploitent actuellement cet outil :

- [Outils Azure Resource Manager (ARM) pour Visual Studio Code](https://github.com/microsoft/vscode-azurearmtools)

- [Blocs-notes .NET interactive](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a>Prise en main : utilisateurs finaux

En général, l’utilisateur final n’a pas besoin d’interagir avec l’outil d’installation de .NET pour les auteurs d’extensions. Si vous rencontrez des problèmes avec l’extension, consultez la [page de résolution des problèmes](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) ou envoyez un problème sur notre [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).
