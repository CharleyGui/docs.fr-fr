---
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
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204514"
---
# <a name="-target-c-compiler-options"></a>-target (Options du compilateur C#)
**L’option compilateur cible** peut être spécifiée dans l’une des quatre formes :  
  
 [-cible:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Pour créer un fichier .exe pour windows 8.x Store applications.  
  
 [/target:exe](./target-exe-compiler-option.md)  
 Pour créer un fichier .exe.  
  
 [/target:library](./target-library-compiler-option.md)  
 Pour créer une bibliothèque de code.  
  
 [-cible:module](./target-module-compiler-option.md)  
 Pour créer un module.  
  
 [/target:winexe](./target-winexe-compiler-option.md)  
 Pour créer un programme Windows.  
  
 [/target:winmdobj](./target-winmdobj-compiler-option.md)  
 Pour créer un fichier .winmdobj intermédiaire.  
  
 Sauf si vous spécifiez **-cible:module**, **-cible** provoque un manifeste d’assemblage cadre .NET à placer dans un fichier de sortie. Pour plus d’informations, voir [Assemblées en .NET](../../../standard/assembly/index.md) et [Attributs communs](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe. Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Le compilateur crée un seul manifeste d’assembly par compilation. Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly. Tous les fichiers de sortie, sauf ceux créés avec **-cible:module** peut contenir un manifeste d’assemblage. Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande. Quel que soit le premier fichier de sortie (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**-target:module**).  
  
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

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (Options du compilateur C#)](./subsystemversion-compiler-option.md)
