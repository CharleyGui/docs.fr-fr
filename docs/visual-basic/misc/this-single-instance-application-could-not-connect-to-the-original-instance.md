---
title: Impossible de connecter cette application à instance unique à l’instance d’origine
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 5585da7f2ccf7d5d3ec8db281ab9534249020a63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619844"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Impossible de connecter cette application à instance unique à l’instance d’origine
Impossible de connecter cette application à instance unique à l'instance d'origine. Ce problème peut avoir les causes suivantes :  
  
- L'instance d'origine a cessé de répondre.  
  
- L'application n'a pas l'autorisation de créer des objets du noyau. Pour plus d’informations sur les objets du noyau, consultez [mutex](../../standard/threading/mutexes.md).  
  
     Le nom de base des objets du noyau est une concaténation entre le GUID de l'assembly, le numéro de la version principale et le numéro de la version secondaire. Le nom de base pourrait être, par exemple, `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Pour corriger cette erreur lors du développement d’une application  
  
1. Vérifiez que l’application continue de répondre.  
  
2. Vérifiez que l’application dispose d’autorisations suffisantes pour créer des objets noyaux.  
  
3. Redémarrez l’instance d’origine de l’application.  
  
4. Redémarrez l’ordinateur pour annuler tout processus susceptible d’utiliser la ressource permettant de se connecter à l’application de l’instance d’origine.  
  
5. Notez les circonstances dans lesquelles l’erreur s’est produite, puis contactez les services de support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi

- [Principes de base du débogueur](/visualstudio/debugger/debugger-basics)
