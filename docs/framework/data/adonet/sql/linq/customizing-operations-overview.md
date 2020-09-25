---
title: "Opérations de personnalisation : Vue d'ensemble"
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d4d375716e3199afcbbb9bbd8b8b04867ca0e5fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173521"
---
# <a name="customizing-operations-overview"></a>Opérations de personnalisation : Vue d'ensemble

Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour les opérations d'insertion, de mise à jour et de suppression selon le mappage. Dans la pratique cependant, vous souhaiterez généralement ajouter votre propre logique métier pour des raisons de sécurité, de validation, etc.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les techniques de personnalisation de ces opérations sont les suivantes :  
  
## <a name="loading-options"></a>Options de chargement  

 Dans vos requêtes, vous pouvez déterminer quelle quantité de données liées à votre cible principale est récupérée lorsque vous vous connectez à la base de données. Cette fonctionnalité est implémentée en grande partie à l'aide de <xref:System.Data.Linq.DataLoadOptions>. Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Méthodes partielles  

 Dans son mappage par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des méthodes partielles qui vous permettent d'implémenter votre logique métier. Pour plus d’informations, consultez [Ajout d’une logique métier à l’aide de méthodes partielles](adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procédures stockées et fonctions définies par l'utilisateur  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge l’utilisation de procédures stockées et de fonctions définies par l’utilisateur. Les procédures stockées sont couramment utilisées pour personnaliser des opérations. Pour plus d’informations, consultez [Procédures stockées](stored-procedures.md).  
  
## <a name="see-also"></a>Voir aussi

- [Personnalisation des opérations d'insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md)
