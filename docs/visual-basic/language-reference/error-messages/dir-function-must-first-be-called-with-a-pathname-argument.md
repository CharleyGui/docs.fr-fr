---
title: La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163426"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’

Un appel initial à la `Dir` fonction n’inclut pas l' `PathName` argument. Le premier appel à `Dir` doit inclure un `PathName` , mais les appels suivants à `Dir` n’ont pas besoin d’inclure des paramètres pour récupérer l’élément suivant.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Fournissez un `PathName` argument dans l’appel de fonction.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
