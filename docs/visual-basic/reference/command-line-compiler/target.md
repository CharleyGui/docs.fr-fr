---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 0ab28d55b2426a4efda112ab84da5e790909d565
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403068"
---
# <a name="-target-visual-basic"></a>-cible (Visual Basic)

Spécifie le format de la sortie du compilateur.

## <a name="syntax"></a>Syntaxe

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Notes

Le tableau suivant résume l’effet de l' `-target` option.

|**Option**|**Comportement**|
|----------------|------------------|
|`-target:exe`|Provoque la création d’une application console exécutable par le compilateur.<br /><br /> Il s’agit de l’option par défaut lorsqu’aucune `-target` option n’est spécifiée. Le fichier exécutable est créé avec une extension. exe.<br /><br /> Sauf spécification contraire avec l' `-out` option, le nom du fichier de sortie prend le nom du fichier d’entrée qui contient la `Sub Main` procédure.<br /><br /> Une seule `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier. exe. Utilisez l' `-main` option du compilateur pour spécifier la classe qui contient la `Sub Main` procédure.|
|`-target:library`|Fait en sorte que le compilateur crée une bibliothèque de liens dynamiques (DLL).<br /><br /> Le fichier de bibliothèque de liens dynamiques est créé avec une extension. dll.<br /><br /> Sauf spécification contraire avec l' `-out` option, le nom du fichier de sortie prend le nom du premier fichier d’entrée.<br /><br /> Lors de la génération d’une DLL, une `Sub Main` procédure n’est pas nécessaire.|
|`-target:module`|Force le compilateur à générer un module qui peut être ajouté à un assembly.<br /><br /> Le fichier de sortie est créé avec une extension. netmodule.<br /><br /> Le common language runtime .NET ne peut pas charger un fichier qui n’a pas d’assembly. Toutefois, vous pouvez incorporer ce type de fichier dans le manifeste d’assembly d’un assembly à l’aide de `-reference` .<br /><br /> Lorsque le code d’un module référence des types internes dans un autre module, les deux modules doivent être incorporés dans un manifeste d’assembly à l’aide de `-reference` .<br /><br /> L’option [-addmodule](addmodule.md) importe les métadonnées d’un module.|
|`-target:winexe`|Provoque la création d’une application Windows exécutable par le compilateur.<br /><br /> Le fichier exécutable est créé avec une extension. exe. Une application basée sur Windows est une application qui fournit une interface utilisateur à partir de la bibliothèque de classes .NET Framework ou avec les API Windows.<br /><br /> Sauf spécification contraire avec l' `-out` option, le nom du fichier de sortie prend le nom du fichier d’entrée qui contient la `Sub Main` procédure.<br /><br /> Une seule `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier. exe. Dans les cas où votre code possède plusieurs classes qui ont une `Sub Main` procédure, utilisez l' `-main` option du compilateur pour spécifier la classe qui contient la `Sub Main` procédure.|
|`-target:appcontainerexe`|Fait en sorte que le compilateur crée une application Windows exécutable qui doit être exécutée dans un conteneur d’application. Ce paramètre est conçu pour être utilisé pour les applications du Windows 8. x Store.<br /><br /> Le paramètre **appcontainerexe** définit un bit dans le champ caractéristiques du fichier [exécutable portable](/windows/desktop/Debug/pe-format) . Ce bit indique que l’application doit être exécutée dans un conteneur d’application. Lorsque ce bit est défini, une erreur se produit si la `CreateProcess` méthode tente de lancer l’application en dehors d’un conteneur d’application. Outre ce paramètre de bit, **-target : appcontainerexe** est équivalent à **-target : winexe**.<br /><br /> Le fichier exécutable est créé avec une extension. exe.<br /><br /> À moins que vous ne spécifiiez autrement à l’aide de l' `-out` option, le nom du fichier de sortie prend le nom du fichier d’entrée qui contient la `Sub Main` procédure.<br /><br /> Une seule `Sub Main` procédure est requise dans les fichiers de code source qui sont compilés dans un fichier. exe. Si votre code contient plusieurs classes qui ont une `Sub Main` procédure, utilisez l' `-main` option du compilateur pour spécifier la classe qui contient la `Sub Main` procédure.|
|`-target:winmdobj`|Fait en sorte que le compilateur crée un fichier intermédiaire que vous pouvez convertir en fichier Windows Runtime binaire (. winmd). Le fichier. winmd peut être consommé par des programmes JavaScript et C++, en plus des programmes en langage managé.<br /><br /> Le fichier intermédiaire est créé avec une extension. winmdobj.<br /><br /> À moins que vous ne spécifiiez autrement à l’aide de l' `-out` option, le nom du fichier de sortie prend le nom du premier fichier d’entrée. Une `Sub Main` procédure n’est pas obligatoire.<br /><br /> Le fichier. winmdobj est conçu pour être utilisé comme entrée pour l' <xref:Microsoft.Build.Tasks.WinMDExp> outil d’exportation afin de produire un fichier de métadonnées Windows (WinMD). Le fichier WinMD a une extension. WinMD et contient à la fois le code de la bibliothèque d’origine et les définitions WinMD que JavaScript, C++ et le Windows Runtime utilisent.|

À moins que vous ne spécifiiez `-target:module` , `-target` provoque l’ajout d’un manifeste d’assembly .NET Framework à un fichier de sortie.

Chaque instance de vbc. exe produit, au plus, un fichier de sortie. Si vous spécifiez une option de compilateur comme `-out` ou `-target` plusieurs fois, le dernier processus du compilateur est mis en vigueur. Des informations sur tous les fichiers d’une compilation sont ajoutées au manifeste. Tous les fichiers de sortie sauf ceux créés avec `-target:module` contiennent les métadonnées de l’assembly dans le manifeste. Utilisez [Ildasm. exe (Désassembleur il)](../../../framework/tools/ildasm-exe-il-disassembler.md) pour afficher les métadonnées dans un fichier de sortie.

La forme abrégée de `-target` est `-t`.

### <a name="to-set--target-in-the-visual-studio-ide"></a>Pour définir-Target dans l’IDE de Visual Studio

1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Application** .

3. Modifiez la valeur dans la zone **type d’application** .

## <a name="example"></a>Exemple

Le code suivant compile `in.vb` , en créant `in.dll` :

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-main](main.md)
- [-out (Visual Basic)](out.md)
- [-Reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [-moduleassemblyname](moduleassemblyname.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
