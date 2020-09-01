---
description: -codepage (Options du compilateur C#)
title: -codepage (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 4c812314ed9c1abcd7d2f34b2281140175621312
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125954"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (Options du compilateur C#)
Cette option spécifie la page de codes à utiliser pendant la compilation si la page exigée n’est pas la page de codes par défaut actuelle du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Identificateur de la page de codes à utiliser pour tous les fichiers de code source de la compilation.  
  
## <a name="remarks"></a>Remarques  
 Le compilateur tente tout d’abord d’interpréter tous les fichiers sources comme des fichiers UTF-8. Si vos fichiers de code source sont encodés dans un format autre que UTF-8 et s’ils utilisent des caractères autres que des caractères ASCII 7 bits, utilisez l’option **-codepage** pour spécifier la page de codes à utiliser. **-codepage** s’applique à tous les fichiers de code source inclus dans votre compilation.  

 Pour plus d’informations sur la façon de savoir quelles pages de codes sont prises en charge sur votre système, consultez [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo).  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
