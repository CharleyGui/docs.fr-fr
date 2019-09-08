---
title: Prise en charge des transactions
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792273"
---
# <a name="transaction-support"></a>Prise en charge des transactions
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]prend en charge trois modèles de transactions distincts. Ces modèles sont présentés ci-dessous dans l'ordre d'exécution des contrôles.  
  
## <a name="explicit-local-transaction"></a>Transaction locale explicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, si la propriété <xref:System.Data.Linq.DataContext.Transaction%2A> a pour valeur une transaction (`IDbTransaction`), l'appel de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est effectué dans le contexte de la même transaction.  
  
 Il vous appartient de valider ou de restaurer la transaction une fois qu’elle s’est correctement exécutée. La connexion qui correspond à la transaction doit être identique à celle utilisée pour construire le <xref:System.Data.Linq.DataContext>. L'utilisation d'une autre connexion lève une exception.  
  
## <a name="explicit-distributable-transaction"></a>Transaction distribuable explicite  
 Vous pouvez appeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] des API (y compris, mais <xref:System.Data.Linq.DataContext.SubmitChanges%2A>sans s’y limiter), dans <xref:System.Transactions.Transaction>l’étendue d’un actif. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]détecte que l’appel se trouve dans l’étendue d’une transaction et ne crée pas de nouvelle transaction. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]évite également de fermer la connexion dans ce cas. Vous pouvez effectuer une requête et exécuter <xref:System.Data.Linq.DataContext.SubmitChanges%2A> dans le contexte de ce type de transaction.  
  
## <a name="implicit-transaction"></a>Transaction implicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vérifie si l’appel se trouve dans la portée d’un <xref:System.Transactions.Transaction> ou si la propriété `Transaction` (`IDbTransaction`) a pour valeur une transaction locale démarrée par l’utilisateur. S’il ne trouve aucune transaction [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , démarre une transaction locale`IDbTransaction`() et l’utilise pour exécuter les commandes SQL générées. Lorsque toutes les commandes SQL ont été exécutées [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] avec succès, valide la transaction locale et retourne.  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [Guide pratique : Mettre en fourchette les envois de données à l’aide de transactions](how-to-bracket-data-submissions-by-using-transactions.md)
