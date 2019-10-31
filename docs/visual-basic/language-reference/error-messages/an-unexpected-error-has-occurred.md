---
title: Une erreur inattendue s'est produite parce qu'une ressource de système d'exploitation requise pour le démarrage de l'instance unique ne peut pas être acquise
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197378"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Une erreur inattendue s'est produite parce qu'une ressource de système d'exploitation requise pour le démarrage de l'instance unique ne peut pas être acquise
L'application n'a pas pu obtenir une ressource nécessaire du système d'exploitation. Ce problème peut avoir certaines des causes suivantes :  
  
- L'application n'est pas autorisée à créer des objets de système d'exploitation nommés.  
  
- Le Common Language Runtime n'est pas autorisé à créer des fichiers mappés sur la mémoire.  
  
- L'application doit accéder à un objet de système d'exploitation, mais un autre processus l'utilise.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez que l'application dispose d'autorisations suffisantes pour créer des objets de système d'exploitation nommés.  
  
2. Veillez à ce que le Common Language Runtime dispose d'autorisations suffisantes pour créer des fichiers mappés sur la mémoire.  
  
3. Redémarrez l'ordinateur pour annuler tout processus susceptible d'utiliser la ressource permettant de se connecter à l'application de l'instance d'origine.  
  
4. Notez les circonstances dans lesquelles l'erreur s'est produite, puis contactez les services de support technique Microsoft  
  
## <a name="see-also"></a>Voir aussi

- [Page Application, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Principes de base du débogueur](/visualstudio/debugger/debugger-basics)
- [Nous contacter](/visualstudio/ide/feedback-options)
