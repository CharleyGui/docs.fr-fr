---
description: '#pragma - Référence C#'
title: '#pragma - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137953"
---
# <a name="pragma-c-reference"></a>#pragma (référence C#)
La directive `#pragma` fournit au compilateur des instructions spéciales pour la compilation du fichier dans lequel elle apparaît. Les instructions doivent être prises en charge par le compilateur. En d’autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées. Le compilateur Microsoft C# prend en charge les deux instructions `#pragma` suivantes :  
  
 [AVERTISSEMENT #pragma](./preprocessor-pragma-warning.md)  
  
 [somme de contrôle #pragma](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Paramètres  
 `pragma-name`  
 Nom d’une directive pragma reconnue.  
  
 `pragma-arguments`  
 Arguments propres à la directive pragma.  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
- [AVERTISSEMENT #pragma](./preprocessor-pragma-warning.md)
- [somme de contrôle #pragma](./preprocessor-pragma-checksum.md)
