---
description: -target (Options du compilateur C#)
title: -target (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 5bfd988e8e399273dbd3292543a3730234c022d6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128554"
---
# <a name="-target-c-compiler-options"></a>-target (Options du compilateur C#)
L’option du compilateur **-target** peut être spécifiée dans l’une des formes suivantes :  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Pour créer un fichier. exe pour les applications du Windows 8. x Store.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Pour créer un fichier .exe.  
  
 [-target:library](./target-library-compiler-option.md)  
 Pour créer une bibliothèque de code.  
  
 [-target:module](./target-module-compiler-option.md)  
 Pour créer un module.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Pour créer un programme Windows.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Pour créer un fichier .winmdobj intermédiaire.  
  
 À moins que vous ne spécifiiez **-target : module**, **-target** entraîne le placement d’un manifeste d’assembly .NET Framework dans un fichier de sortie. Pour plus d’informations, consultez [assemblys dans .net](../../../standard/assembly/index.md) et [attributs communs](../attributes/global.md).  
  
 Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe. Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Le compilateur crée un seul manifeste d’assembly par compilation. Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly. Tous les fichiers de sortie sauf ceux créés avec **-target : module** peuvent contenir un manifeste d’assembly. Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande. Quel que soit le premier fichier de sortie (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**-target:module**).  
  
 Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme CLS avec l’attribut <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Pour plus d’informations sur la définition de cette option de compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (Options du compilateur C#)](./subsystemversion-compiler-option.md)
