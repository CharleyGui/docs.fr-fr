---
title: Réduction des dépendances de package avec project.json
description: Réduisez les dépendances de package dans le cadre de la création de bibliothèques project.json.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740828"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Réduction des dépendances de package avec project.json

Cet article décrit ce que vous devez savoir sur la réduction de vos dépendances de package lors de la création de bibliothèques `project.json`. À la fin de cet article, vous saurez comment composer votre bibliothèque de sorte qu’elle utilise seulement les dépendances dont elle a besoin.

## <a name="why-its-important"></a>Pourquoi c’est important

.NET Core est un produit composé de packages NuGet.  Parmi les packages essentiels figure le [métapackage .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), un package NuGet composé d’autres packages. Il vous fournit l’ensemble de paquets qui sont garantis pour travailler sur plusieurs implémentations .NET, tels que .NET Framework, .NET Core, et Xamarin/Mono.

Cependant, il est probable que votre bibliothèque n’utilise pas chaque package individuel qu’il contient.  Lors de la création d’une bibliothèque et de sa distribution sur NuGet, il est conseillé de « réduire » vos dépendances aux seuls packages que vous utilisez.  Ceci aboutit à un encombrement global inférieur pour les packages NuGet.

## <a name="how-to-do-it"></a>Marche à suivre

Actuellement, il n’y a pas de commande officielle `dotnet` qui coupe les références de paquet.  Vous devez donc le faire manuellement.  Le processus général se présente comme suit :

1. Faites référence à `NETStandard.Library` version `1.6.0` dans une section `dependencies` de votre fichier `project.json`.
2. Restaurez les packages avec `dotnet restore` ([voir la remarque](#dotnet-restore-note)) à partir de la ligne de commande.
3. Parcourez le fichier `project.lock.json` et recherchez la section `NETStandard.Library`.  Elle est au début du fichier.
4. Copiez tous les packages répertoriés sous `dependencies`.
5. Supprimez la référence à `.NETStandard.Library` et remplacez-la par les packages copiés.
6. Supprimez les références aux packages dont vous n’avez pas besoin.

Vous pouvez déterminer les packages dont vous n’avez pas besoin de l’une des façons suivantes :

1. Essai et erreur. Ceci implique de supprimer un package, de le restaurer, de déterminer si votre bibliothèque se compile encore et de répéter ce processus.
2. L’utilisation d’un outil comme [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) permet d’examiner les références pour voir ce que votre code utilise réellement. Vous pouvez ensuite supprimer les paquets qui ne correspondent pas aux types que vous utilisez.

## <a name="example"></a> Exemple

Imaginez que vous avez écrit une bibliothèque qui fournissait des fonctionnalités supplémentaires aux types de collecte génériques. Ce type de bibliothèque doit dépendre de packages comme `System.Collections`, mais peut ne pas du tout dépendre de packages comme `System.Net.Http`. Par conséquent, il serait judicieux de réduire les dépendances des packages aux seuls packages dont cette bibliothèque a besoin !

Pour réduire cette bibliothèque, vous commencez par le fichier `project.json` et vous ajoutez une référence à `NETStandard.Library` version `1.6.0`.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Ensuite, vous restaurez les packages avec `dotnet restore` ([voir la remarque](#dotnet-restore-note)), vous examinez le fichier `project.lock.json` et vous recherchez tous les packages restaurés pour `NETStandard.Library`.

Voici à quoi ressemble la section appropriée du fichier `project.lock.json` quand vous ciblez `netstandard1.0` :

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Ensuite, copiez les références de package dans la section `dependencies` du fichier `project.json` de la bibliothèque, en remplaçant la référence `NETStandard.Library` :

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

Cela représente beaucoup de packages, dont la plupart ne sont certainement pas nécessaires pour étendre les types de collections.  Vous pouvez supprimer manuellement les packages ou utiliser un outil comme [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) pour identifier les packages utilisés par votre code.

Voici ce à quoi un package réduit peut ressembler :

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Il a maintenant un encombrement moindre que s’il dépendait du métapackage `NETStandard.Library`.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
