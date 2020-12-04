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
# <a name="net-install-tool-for-extension-authors"></a><span data-ttu-id="7ae2b-103">Outil d’installation .NET pour les auteurs d’extensions</span><span class="sxs-lookup"><span data-stu-id="7ae2b-103">.NET install tool for extension authors</span></span>

<span data-ttu-id="7ae2b-104">L' [outil d’installation de .net pour les auteurs d’extensions](https://github.com/dotnet/vscode-dotnet-runtime) est une extension de Visual Studio code qui permet d’acquérir le Runtime .net spécifiquement pour les auteurs d’extensions vs code.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-104">The [.NET install tool for extension authors](https://github.com/dotnet/vscode-dotnet-runtime) is a Visual Studio Code extension that allows acquisition of the .NET runtime specifically for VS Code extension authors.</span></span> <span data-ttu-id="7ae2b-105">Cet outil est conçu pour être utilisé dans les extensions écrites en .NET et nécessiter .NET pour démarrer des éléments de l’extension (par exemple, un serveur de langage).</span><span class="sxs-lookup"><span data-stu-id="7ae2b-105">This tool is intended to be leveraged in extensions that are written in .NET and require .NET to boot pieces of the extension (for example, a language server).</span></span> <span data-ttu-id="7ae2b-106">L’extension n’est pas destinée à être utilisée directement par les utilisateurs pour installer .NET en vue du développement.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-106">The extension is not intended to be used directly by users to install .NET for development.</span></span>

## <a name="getting-started-extension-authors"></a><span data-ttu-id="7ae2b-107">Prise en main : auteurs d’extensions</span><span class="sxs-lookup"><span data-stu-id="7ae2b-107">Getting started: extension authors</span></span>

<span data-ttu-id="7ae2b-108">Pour vous assurer que l’outil d’installation de .NET pour les auteurs d’extensions est adapté à votre scénario, commencez par examiner les [objectifs de cette extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) sur notre page github.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-108">To ensure that the .NET install tool for extension authors is the right fit for your scenario, start by reviewing the [goals of this extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) on our GitHub page.</span></span>

> [!NOTE]
> <span data-ttu-id="7ae2b-109">Cet outil peut être utilisé pour installer uniquement le Runtime .NET, mais il n’a actuellement pas la possibilité d’installer le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-109">This tool can be used to install the .NET runtime only, it currently does not have the capability to install the .NET SDK.</span></span>

<span data-ttu-id="7ae2b-110">Une fois que vous avez vérifié que l’outil d’installation de .NET pour les auteurs d’extensions répond à vos besoins, vous pouvez en dépendre dans votre [manifeste d’extension](https://code.visualstudio.com/api/references/extension-manifest) et commencer à utiliser les commandes exposées avec l' [API vs code](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span><span class="sxs-lookup"><span data-stu-id="7ae2b-110">Once you have verified that the .NET install tool for extension authors fits your needs, you can take a dependency on it in your [extension manifest](https://code.visualstudio.com/api/references/extension-manifest) and begin using the commands we expose with the [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span></span> <span data-ttu-id="7ae2b-111">Vous pouvez trouver la liste des commandes exposées par cette extension sur notre [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).</span><span class="sxs-lookup"><span data-stu-id="7ae2b-111">You can find the list of commands this extension exposes on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).</span></span>

<span data-ttu-id="7ae2b-112">Consultez cet [exemple d’extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) pour voir ces étapes en action.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-112">Check out this [sample extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) to see these steps in action.</span></span>

<span data-ttu-id="7ae2b-113">Pour obtenir plus d’exemples, consultez ces extensions open source qui exploitent actuellement cet outil :</span><span class="sxs-lookup"><span data-stu-id="7ae2b-113">For more examples, check out these open source extensions that currently leverage this tool:</span></span>

- [<span data-ttu-id="7ae2b-114">Outils Azure Resource Manager (ARM) pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7ae2b-114">Azure Resource Manager (ARM) Tools for Visual Studio Code</span></span>](https://github.com/microsoft/vscode-azurearmtools)

- [<span data-ttu-id="7ae2b-115">Blocs-notes .NET interactive</span><span class="sxs-lookup"><span data-stu-id="7ae2b-115">.NET Interactive Notebooks</span></span>](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a><span data-ttu-id="7ae2b-116">Prise en main : utilisateurs finaux</span><span class="sxs-lookup"><span data-stu-id="7ae2b-116">Getting started: end users</span></span>

<span data-ttu-id="7ae2b-117">En général, l’utilisateur final n’a pas besoin d’interagir avec l’outil d’installation de .NET pour les auteurs d’extensions.</span><span class="sxs-lookup"><span data-stu-id="7ae2b-117">In general, the end user should not need to interact with the .NET install tool for extension authors at all.</span></span> <span data-ttu-id="7ae2b-118">Si vous rencontrez des problèmes avec l’extension, consultez la [page de résolution des problèmes](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) ou envoyez un problème sur notre [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span><span class="sxs-lookup"><span data-stu-id="7ae2b-118">If you are having problems with the extension, check out our [troubleshooting page](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) or file an issue on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span></span>
