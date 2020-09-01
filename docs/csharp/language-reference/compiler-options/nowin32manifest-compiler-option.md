---
description: -nowin32manifest (Options du compilateur C#)
title: -nowin32manifest (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125057"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (Options du compilateur C#)
Utilisez l’option **-nowin32manifest** pour indiquer au compilateur de ne pas incorporer le manifeste de l’application dans le fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Notes  
 Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.  
  
 Dans Visual Studio, définissez cette option dans la page de propriétés **Application** en sélectionnant l’option **Créer une application sans fichier manifeste** dans la zone de liste déroulante **Manifeste**. Pour plus d’informations, consultez [page application, concepteur de projets (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Pour plus d’informations sur la création d’un manifeste, consultez [-win32manifest (options du compilateur C#)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
