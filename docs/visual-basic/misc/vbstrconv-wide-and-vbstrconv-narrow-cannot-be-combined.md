---
title: Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: e90af8ba91872a04be11524753d9df0d168315ca
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198246"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a>Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow
Votre application essaie de combiner les membres de l’énumération `VbStrConv` `Wide` et `Narrow`, qui s’excluent mutuellement.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Supprimez `VbStrConv.Wide` ou `VbStrConv.Narrow`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization>

- [Développer des applications mondialisées et localisées](/visualstudio/ide/globalizing-and-localizing-applications)
