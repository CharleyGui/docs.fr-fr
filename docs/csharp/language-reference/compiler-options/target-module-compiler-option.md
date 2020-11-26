---
description: -target:module (Options du compilateur C#)
title: -target:module (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193606"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (Options du compilateur C#)

Cette option empêche le compilateur de générer un manifeste d’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Notes  

 Par défaut, le fichier de sortie créé en effectuant une compilation avec cette option porte l’extension .netmodule.  
  
 Un fichier qui n’a pas de manifeste d’assembly ne peut pas être chargé par le Runtime .NET. Cependant, un tel fichier peut être incorporé dans le manifeste d’un assembly au moyen de [-addmodule](./addmodule-compiler-option.md).  
  
 Si plusieurs modules sont créés dans une seule compilation, les types [internal](../keywords/internal.md) d’un module sont accessibles à d’autres modules dans la compilation. Quand le code d’un module référence des types `internal` dans un autre module, les deux modules doivent être incorporés dans un manifeste d’assembly au moyen de **-addmodule**.  
  
 La création d’un module n’est pas prise en charge dans l’environnement de développement Visual Studio.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemple  

 Compilez `in.cs`, en créant `in.netmodule` :  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [-Target (options du compilateur C#)](./target-compiler-option.md)
- [Options du compilateur C#](./index.md)
