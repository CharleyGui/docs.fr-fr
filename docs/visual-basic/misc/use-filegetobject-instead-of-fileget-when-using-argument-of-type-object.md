---
title: Utilisez 'FileGetObject' à la place de 'FileGet' quand l’argument est de type 'Object'.
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059403"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Utilisez 'FileGetObject' à la place de 'FileGet' quand l’argument est de type 'Object'.

La méthode `FileGet` comprend un argument de type `Object`. `FileGetObject` doit être utilisé à la place de `FileGet` pour éviter toute ambiguïté.  
  
 Notez que les fonctionnalités offertes par `My.Computer.Filesystem` proposent une plus grande facilité d’utilisation et des performances accrues par rapport à `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Remplacez `FileGet` par `FileGetObject`.  
  
2. Convertissez l’argument `Object` en type plus spécifique.  
  
## <a name="see-also"></a>Voir aussi

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
