---
title: La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874460"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’

Un appel initial à la `Dir` fonction n’inclut pas l' `PathName` argument. Le premier appel à `Dir` doit inclure un `PathName` , mais les appels suivants à `Dir` n’ont pas besoin d’inclure des paramètres pour récupérer l’élément suivant.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Fournissez un `PathName` argument dans l’appel de fonction.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
