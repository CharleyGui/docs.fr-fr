---
title: Utilisez ’FilePutObject’ à la place de ’FilePut’ quand l’argument est de type ’Object’.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100332"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Utilisez ’FilePutObject’ à la place de ’FilePut’ quand l’argument est de type ’Object’.

La méthode `FilePut` comprend un argument de type `Object`. `FilePutObject` doit être utilisé à la place de `FilePut` pour éviter toute ambiguïté.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Remplacez `FilePut` par `FilePutObject`.  
  
- Convertissez l’argument `Object` en type plus spécifique.  
  
- Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Voir aussi

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My. Computer. FileSystem. WriteAllBytes,](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
