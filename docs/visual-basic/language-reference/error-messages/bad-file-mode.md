---
title: Mode de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409867"
---
# <a name="bad-file-mode"></a>Mode de fichier incorrect
Les instructions utilisées pour manipuler le contenu d’un fichier doivent être appropriées au mode dans lequel le fichier a été ouvert. Les causes possibles sont les suivantes :  
  
- Une `FilePutObject` `FileGetObject` instruction ou spécifie un fichier séquentiel.  
  
- Une `Print` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Output` ou `Append` .  
  
- Une `Input` instruction spécifie un fichier ouvert pour un mode d’accès autre que`Input`  
  
- Tentative d’écriture dans un fichier en lecture seule.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous `FilePutObject` `FileGetObject` que et ne font référence qu’à des fichiers ouverts pour `Random` ou `Binary` accessibles.  
  
- Assurez-vous que `Print` spécifie un fichier ouvert pour le `Output` `Append` mode d’accès ou. Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
- Assurez-vous que `Input` spécifie un fichier ouvert pour `Input` . Si ce n’est pas le cas, utilisez une autre instruction pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
- Si vous écrivez dans un fichier en lecture seule, modifiez l’état de lecture/écriture du fichier ou n’essayez pas d’écrire dans celui-ci.  
  
- Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem>
- [Résolution des problèmes : lecture et écriture dans des fichiers texte](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
