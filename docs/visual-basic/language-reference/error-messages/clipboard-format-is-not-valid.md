---
title: Format de Presse-papiers non valide
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874584"
---
# <a name="clipboard-format-is-not-valid"></a>Format de Presse-papiers non valide

Le format de presse-papiers spécifié est incompatible avec la méthode en cours d’exécution. Cette erreur peut avoir plusieurs causes :  
  
- Utilisation de la méthode ou du presse-papiers `GetText` `SetText` avec un format de presse-papiers autre que `vbCFText` ou `vbCFLink` .  
  
- Utilisation de la méthode ou du presse-papiers `GetData` `SetData` avec un format de presse-papiers autre que `vbCFBitmap` , `vbCFDIB` ou `vbCFMetafile` .  
  
- L’utilisation `GetData` `SetData` des méthodes ou d’un `DataObject` avec un format de presse-papiers dans la plage réservée par Microsoft Windows pour les formats enregistrés (&HC000-&HFFFF), lorsque ce format de presse-papiers n’a pas été inscrit auprès de Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez le format non valide et spécifiez un format valide.  
  
## <a name="see-also"></a>Voir aussi

- [Presse-papiers : ajout d’autres formats](/cpp/mfc/clipboard-adding-other-formats)
