---
description: -noconfig (Options du compilateur C#)
title: -noconfig (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 26d0680743ccc3af26a0e81eeec9cd2fc0d693af
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125226"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (Options du compilateur C#)
L’option **-noconfig** indique au compilateur de ne pas compiler avec le fichier csc. rsp, qui se trouve dans le même répertoire que le fichier csc.exe et est chargé à partir de celui-ci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Notes  
 Le fichier csc.rsp fait référence à tous les assemblys fournis avec le .NET Framework. Les références réelles qui sont incluses dans l’environnement de développement Visual Studio .NET varient en fonction du type de projet.  
  
 Vous pouvez modifier le fichier csc. RSP et spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation à partir de la ligne de commande avec csc.exe (à l’exception de l’option **-noconfig** ).  
  
 Le compilateur traite les options passées à la commande **csc** en dernier. De ce fait, toute option sur la ligne de commande se substitue au paramètre de la même option dans le fichier csc.rsp.  
  
 Si vous ne souhaitez pas que le compilateur recherche et utilise les paramètres dans le fichier csc. rsp, spécifiez **-noconfig**.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
