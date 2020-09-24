---
description: '#else - Référence C#'
title: '#else - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: f0dc8c34672c3e9e5a2207211794fbc8099640c5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168671"
---
# <a name="else-c-reference"></a>#else (référence C#)

`#else` vous permet de créer une directive conditionnelle composée de sorte que si aucune des expressions contenues dans les précédentes directives [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md) (facultatif) n’a la valeur `true`, le compilateur évalue l’ensemble du code entre `#else` et la directive `#endif` suivante.  
  
## <a name="remarks"></a>Notes  

 [#endif](./preprocessor-endif.md) doit être la directive de préprocesseur suivante après `#else`. Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#else`.  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
