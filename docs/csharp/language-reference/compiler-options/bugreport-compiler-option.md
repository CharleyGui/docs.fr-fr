---
description: -bugreport (Options du compilateur C#)
title: -bugreport (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 1fb2efc9b12680e95767746c7e4e1ddacbdd2594
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281504"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (Options du compilateur C#)

Spécifie que les informations de débogage doivent être placées dans un fichier pour une future analyse.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  

 `file`  
 Nom du fichier qui doit contenir votre rapport de bogues.  
  
## <a name="remarks"></a>Notes  

 L’option **-bugreport** spécifie que les informations suivantes doivent être placées dans `file` :  
  
- Une copie de tous les fichiers de code source de la compilation.  
  
- Une liste des options du compilateur utilisées dans la compilation.  
  
- Les informations de version concernant votre compilateur, votre runtime et votre système d’exploitation.  
  
- Les assemblys et les modules référencés, enregistrés sous forme de chiffres hexadécimaux, à l’exception des assemblys qui sont fournis avec .NET et le kit de développement logiciel (SDK) .NET.  
  
- Les résultats de la compilation, le cas échéant.  
  
- Une description du problème, qui vous sera demandée.  
  
- Une description de vos suggestions de résolution du problème, qui vous sera demandée.  
  
 Si cette option est utilisée avec **-errorreport:prompt** ou **-errorreport:send** , les informations figurant dans le fichier seront envoyées à Microsoft Corporation.  
  
 Étant donné qu’une copie de tous les fichiers de code source sera placée dans `file`, vous souhaiterez peut-être reproduire l’erreur de code suspecte dans le programme le plus court possible.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
 Notez que le contenu du fichier généré expose le code source, ce qui pourrait entraîner une divulgation d’informations non voulue.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [-errorReport (options du compilateur C#)](./errorreport-compiler-option.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
