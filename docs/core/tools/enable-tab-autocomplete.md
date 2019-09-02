---
title: Activer la saisie semi-automatique via la touche TAB
description: Cet article vous explique comment activer la saisie semi-automatique via la touche TAB pour l’interface CLI .NET Core dans PowerShell, Bash et zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: c7673d95f3710d78d3a09b26f031396587f9c669
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202492"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="c9dec-103">Guide pratique pour activer la saisie semi-automatique à l’aide de la touche TAB pour l’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9dec-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="c9dec-104">À compter du SDK .NET Core 2.0, l’interface CLI .NET Core prend en charge la saisie semi-automatique via la touche TAB.</span><span class="sxs-lookup"><span data-stu-id="c9dec-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="c9dec-105">Cet article décrit comment configurer la saisie semi-automatique via la touche TAB pour trois des interpréteurs de commandes : PowerShell, Bash et zsh.</span><span class="sxs-lookup"><span data-stu-id="c9dec-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="c9dec-106">D’autres interpréteurs de commandes peuvent prendre en charge la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="c9dec-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="c9dec-107">Consultez leur documentation pour configurer la saisie semi-automatique ; les étapes devraient être similaires à la procédure décrite dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c9dec-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="c9dec-108">Une fois activée, la complétion par la touche Tab dans l’interface CLI .NET Core se déclenche en tapant une commande `dotnet` dans l’interpréteur de commandes, puis en appuyant sur la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="c9dec-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="c9dec-109">La ligne de commande actuelle est envoyée à la commande `dotnet complete`, et les résultats sont traités par votre interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="c9dec-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="c9dec-110">Vous pouvez tester les résultats sans activer la saisie semi-automatique via la touche TAB en envoyant une instruction directement à la commande `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="c9dec-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="c9dec-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c9dec-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="c9dec-112">Si cette commande ne fonctionne pas, vérifiez que le kit SDK .NET Core 2.0 ou version ultérieure est installée.</span><span class="sxs-lookup"><span data-stu-id="c9dec-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="c9dec-113">S’il est installé mais que cette commande ne fonctionne toujours pas, vérifiez que la commande `dotnet` correspond à la version 2.0 ou ultérieure du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9dec-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="c9dec-114">Utilisez la commande `dotnet --version` pour afficher la version de `dotnet` correspondant à votre chemin d’accès actuel.</span><span class="sxs-lookup"><span data-stu-id="c9dec-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="c9dec-115">Pour plus d’informations, consultez [Sélectionner la version .NET Core à utiliser](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="c9dec-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="c9dec-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="c9dec-116">Examples</span></span>

<span data-ttu-id="c9dec-117">Voici quelques exemples de saisie semi-automatique via la touche TAB :</span><span class="sxs-lookup"><span data-stu-id="c9dec-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="c9dec-118">Entrée</span><span class="sxs-lookup"><span data-stu-id="c9dec-118">Input</span></span>                                | <span data-ttu-id="c9dec-119">devient</span><span class="sxs-lookup"><span data-stu-id="c9dec-119">becomes</span></span>                                                                     | <span data-ttu-id="c9dec-120">car</span><span class="sxs-lookup"><span data-stu-id="c9dec-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="c9dec-121">`add` est la première sous-commande, par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="c9dec-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="c9dec-122">La saisie semi-automatique renvoie des sous-chaînes et `--help` s’affiche en premier, par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="c9dec-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="c9dec-123">Une seconde pression sur la touche TAB fait apparaître la suggestion suivante.</span><span class="sxs-lookup"><span data-stu-id="c9dec-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="c9dec-124">Les résultats s’affichent par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="c9dec-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="c9dec-125">La saisie semi-automatique via la touche TAB tient compte du fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="c9dec-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="c9dec-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9dec-126">PowerShell</span></span>

<span data-ttu-id="c9dec-127">Pour ajouter la saisie semi-automatique via la touche TAB à **PowerShell** pour l’interface CLI .NET Core, créez ou modifiez le profil stocké dans la variable `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="c9dec-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="c9dec-128">Pour plus d’informations, consultez [Création de votre profil](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) et [Profils et stratégie d’exécution](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="c9dec-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="c9dec-129">Ajoutez le code suivant à votre profil :</span><span class="sxs-lookup"><span data-stu-id="c9dec-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="c9dec-130">Bash</span><span class="sxs-lookup"><span data-stu-id="c9dec-130">Bash</span></span>

<span data-ttu-id="c9dec-131">Pour ajouter la saisie semi-automatique via la touche TAB à votre interpréteur de commandes **bash** pour l’interface CLI .NET Core, ajoutez le code suivant à votre fichier `.bashrc` :</span><span class="sxs-lookup"><span data-stu-id="c9dec-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="c9dec-132">Zsh</span><span class="sxs-lookup"><span data-stu-id="c9dec-132">Zsh</span></span>

<span data-ttu-id="c9dec-133">Pour ajouter la saisie semi-automatique via la touche TAB à votre interpréteur de commandes **zsh** pour l’interface CLI .NET Core, ajoutez le code suivant à votre fichier `.zshrc` :</span><span class="sxs-lookup"><span data-stu-id="c9dec-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
