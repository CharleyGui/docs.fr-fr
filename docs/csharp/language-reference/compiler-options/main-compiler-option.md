---
description: -main (Options du compilateur C#)
title: -main (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 61e63de8082a335b448ffee1ae35170d3a1cf6b4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125265"
---
# <a name="-main-c-compiler-options"></a>-main (Options du compilateur C#)

Cette option spécifie la classe qui contient le point d’entrée du programme dans le cas où plusieurs classes contiennent une méthode **Main**.

## <a name="syntax"></a>Syntaxe

```console
-main:class
```

## <a name="arguments"></a>Arguments
 `class`  
 Type contenant la méthode **Main**.  
 Le nom de classe fourni doit être complet, c’est-à-dire qu’il doit inclure l’espace de noms complet contenant la classe, suivi du nom de classe. Par exemple, si la méthode `Main` se trouve dans la classe `Program` dans l’espace de noms `MyApplication.Core`, l’option du compilateur doit être `-main:MyApplication.Core.Program`.

## <a name="remarks"></a>Remarques

Si votre compilation comprend plusieurs types avec une méthode [Main](../../programming-guide/main-and-command-args/index.md), vous pouvez spécifier le type qui contient la méthode **Main** à utiliser comme point d’entrée dans le programme.

Cette option est destinée à être utilisée lors de la compilation d’un fichier *. exe* .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la page **Propriétés** du projet.

2. Cliquez sur la page de propriétés **Application**.

3. Modifiez la propriété **Objet de démarrage**.

    Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Pour définir cette option du compilateur en modifiant manuellement le fichier *. csproj*

Vous pouvez définir cette option en modifiant le fichier. csproj et en ajoutant un élément `StartupObject` à l’intérieur de la `PropertyGroup` section. Par exemple :

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Exemple

Compilez `t2.cs` et `t3.cs`, en spécifiant que la **Main** se trouve dans `Test2` :

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
