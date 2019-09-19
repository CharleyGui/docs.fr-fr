---
title: Options F# Interactive
description: En savoir plus sur les options de ligne de F# commande prises en charge par Interactive, FSI. exe.
ms.date: 05/16/2016
ms.openlocfilehash: c9cd5c2e73a6e2f6ce0a9b2f2a631b6a2658423c
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083117"
---
# <a name="f-interactive-options"></a>Options F# Interactive

> [!NOTE]
> Cet article ne traite pour le moment que de l’expérience Windows.  Il va être réécrit.

Cette rubrique décrit les options de ligne de commande prises F# en charge `fsi.exe`par Interactive,. F#Interactive accepte un grand nombre des mêmes options de ligne de F# commande que le compilateur, mais il accepte également quelques options supplémentaires.

## <a name="using-f-interactive-for-scripting"></a>Utilisation F# d’interactive pour l’écriture de scripts
F#Interactive, `fsi.exe`, peut être lancé de manière interactive ou peut être lancé à partir de la ligne de commande pour exécuter un script. La syntaxe de la ligne de commande est

```console
> fsi.exe [options] [ script-file [arguments] ]
```

L’extension de fichier F# pour les fichiers `.fsx`de script est.

## <a name="table-of-f-interactive-options"></a>Tableau des F# options interactives
Le tableau suivant récapitule les options prises en charge F# par interactive. Vous pouvez définir ces options sur la ligne de commande ou via l’IDE de Visual Studio. Pour définir ces options dans l’IDE de Visual Studio, ouvrez le menu **Outils** , sélectionnez **options...** , puis développez le  **F# nœud Outils** et sélectionnez  **F# interactif**.

Quand des listes apparaissent F# dans des arguments d’option interactive, les éléments de liste sont`;`séparés par des points-virgules ().

|Option|Description|
|------|-----------|
|**--**|Permet d’indiquer F# à interactive de traiter les arguments restants comme des F# arguments de ligne de commande pour le programme ou le script, auquel vous pouvez accéder dans le code à l’aide de la liste **FSI. CommandLineArgs**.|
|**--checked**[ **+** &#124; **-** ]|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--CodePage :&lt;int&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--consolecolors**[ **+** &#124; **-** ]|Génère des messages d’avertissement et d’erreur en couleur.|
|**--crossoptimize**[ **+** &#124; **-** ]|Activez ou désactivez les optimisations entre modules.|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--debug:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--define :&lt;chaîne&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--deterministic**[ **+** &#124; **-** ]|Produit un assembly déterministe (y compris le GUID de la version du module et l’horodateur).|
|**--exec**|Indique à F# interactive de quitter après le chargement des fichiers ou d’exécuter le fichier de script spécifié sur la ligne de commande.|
|**--fullpaths**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--gui**[ **+** &#124; **-** ]|Active ou désactive la boucle d’événements Windows Forms. Les styles sont activés par défaut.|
|**--help**<br /><br />**-?**|Utilisé pour afficher la syntaxe de la ligne de commande et une brève description de chaque option.|
|**--lib :&lt;Folder-List&gt;**<br /><br />**-I :&lt;dossier-liste&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--Load :&lt;nom de fichier&gt;**|Compile le code source donné au démarrage et charge les constructions compilées F# dans la session. Si la source cible contient des directives de script telles que **#use** ou **#load**, vous devez utiliser **--use** ou **#use** à la place de **--Load** ou **#load**.|
|**--mlcompatibility**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--noframework**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez [Options du compilateur](compiler-options.md)|
|**--nologo**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--nowarn:&lt;warning-list&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--optimize**[ **+** &#124; **-** ]|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--preferreduilang:&lt;lang&gt;**| Spécifie le nom de culture de la langue de sortie par défaut (par exemple, es-ES, ja-JP). |
|**--quiet**|Supprime F# la sortie interactive du flux **stdout** .|
|**--quotations-debug**|Spécifie que des informations de débogage supplémentaires doivent être émises pour les expressions dérivées des littéraux de F# quotation et des définitions réfléchies. Les informations de débogage sont ajoutées aux attributs personnalisés d' F# un nœud d’arborescence d’expression. Consultez [Quotations de code](code-quotations.md) et [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[ **+** &#124; **-** ]|Activez ou désactivez la saisie semi-automatique par tabulation en mode interactif.|
|**--Référence :&lt;nom de fichier&gt;**<br /><br />**-r :&lt;nom_fichier&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|Empêche le verrouillage des références par le F# processus interactif.|
|**--simpleresolution**|Résout les références d’assembly à l’aide de règles basées sur le répertoire plutôt que sur la résolution MSBuild.|
|**--tailcalls**[ **+** &#124; **-** ]|Activez ou désactivez l’utilisation de l’instruction IL tail, qui entraîne la réutilisation du frame de pile pour les fonctions récursives tail. Cette option est activée par défaut.|
|**--TargetProfile :&lt;chaîne&gt;**|Spécifie le profil du Framework cible de cet assembly. Les valeurs valides sont mscorlib, Netcore ou netstandard.  La valeur par défaut est mscorlib.|
|**--Use :&lt;nom_fichier&gt;**|Indique à l’interpréteur d’utiliser le fichier donné au démarrage comme entrée initiale.|
|**--utf8output**|Identique à l’option de compilateur FSC. exe. Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--Warn :&lt;Warning-niveau&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-list&gt;**|Identique à l’option de compilateur **FSC. exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----|-----------|
|[Options du compilateur](compiler-options.md)|Décrit les options de ligne de commande F# disponibles pour le compilateur **FSC. exe**.|
