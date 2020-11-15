---
title: Activer la saisie semi-automatique via la touche Tab
description: Cet article explique comment activer la saisie semi-automatique via la touche Tab pour la CLI .NET pour PowerShell, bash et zsh.
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: 31bf5e74644680fc30ca5b79972fbed6367363e1
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634010"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a>Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Cet article décrit comment configurer la saisie semi-automatique via la touche TAB pour trois des interpréteurs de commandes : PowerShell, Bash et zsh. Pour les autres shells, reportez-vous à leur documentation sur la configuration de la saisie semi-automatique par tabulation.

Une fois la configuration terminée, la saisie semi-automatique via la touche Tab pour l’interface CLI .NET est déclenchée en tapant une `dotnet` commande dans l’interpréteur de commandes, puis en appuyant sur la touche Tab. La ligne de commande actuelle est envoyée à la commande `dotnet complete`, et les résultats sont traités par votre interpréteur de commandes. Vous pouvez tester les résultats sans activer la saisie semi-automatique via la touche TAB en envoyant une instruction directement à la commande `dotnet complete`. Par exemple :

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Si cette commande ne fonctionne pas, vérifiez que le kit SDK .NET Core 2.0 ou version ultérieure est installée. S’il est installé mais que cette commande ne fonctionne toujours pas, vérifiez que la commande `dotnet` correspond à la version 2.0 ou ultérieure du SDK .NET Core. Utilisez la commande `dotnet --version` pour afficher la version de `dotnet` correspondant à votre chemin d’accès actuel. Pour plus d’informations, consultez [Sélectionner la version .net à utiliser](../versions/selection.md).

### <a name="examples"></a>Exemples

Voici quelques exemples de saisie semi-automatique via la touche TAB :

Entrée                                | devient                                                                     | car
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` est la première sous-commande, par ordre alphabétique.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | La saisie semi-automatique renvoie des sous-chaînes et `--help` s’affiche en premier, par ordre alphabétique.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Une seconde pression sur la touche TAB fait apparaître la suggestion suivante.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Les résultats s’affichent par ordre alphabétique.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | La saisie semi-automatique via la touche TAB tient compte du fichier de projet.

## <a name="powershell"></a>PowerShell

Pour ajouter la saisie semi-automatique via la touche Tab à **PowerShell** pour l’interface CLI .net, créez ou modifiez le profil stocké dans la variable `$PROFILE` . Pour plus d’informations, consultez [Création de votre profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) et [Profils et stratégie d’exécution](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).

Ajoutez le code suivant à votre profil :

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>bash

Pour ajouter la saisie semi-automatique via la touche Tab à votre interpréteur de commandes **bash** pour l’interface de commande .net, ajoutez le code suivant à votre `.bashrc` fichier :

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zsh

Pour ajouter la saisie semi-automatique via la touche Tab à votre shell **zsh** pour l’interface de commande .net, ajoutez le code suivant à votre `.zshrc` fichier :

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
