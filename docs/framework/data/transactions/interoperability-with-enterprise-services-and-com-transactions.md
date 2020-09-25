---
title: Interopérabilité avec Enterprise Services et les transactions COM+
description: Comprendre l’interopérabilité avec Enterprise Services et les transactions COM+ dans .NET à l’aide de l’espace de noms System. transactions.
ms.date: 03/30/2017
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
ms.openlocfilehash: 48cb006a4294b7c43de262eb2d19c6c4ea9d22fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186768"
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Interopérabilité avec Enterprise Services et les transactions COM+

L'espace de noms <xref:System.Transactions> prend en charge l'interopérabilité entre les objets de transaction créés à l'aide de cet espace de noms et les transactions créées via COM+.  
  
 Vous pouvez utiliser l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> lors de la création d'une nouvelle instance <xref:System.Transactions.TransactionScope> pour spécifier le niveau d'interopérabilité avec COM+.  
  
 Par défaut, lorsque votre code d’application vérifie la <xref:System.Transactions.Transaction.Current%2A> propriété statique, <xref:System.Transactions> tente de rechercher une transaction qui est autrement en cours ou un <xref:System.Transactions.TransactionScope> objet qui dicte que <xref:System.Transactions.Transaction.Current%2A> a la **valeur null**. S'il n'en détecte pas, <xref:System.Transactions> recherche une transaction dans le contexte COM+. Notez que même si <xref:System.Transactions> détecte une transaction à partir du contexte COM+, il privilégie les transactions natives de <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Niveaux d'interopérabilité  

 L'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> définit les niveaux d'interopérabilité suivants : <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> et <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 La classe <xref:System.Transactions.TransactionScope> fournit des constructeurs qui acceptent <xref:System.Transactions.EnterpriseServicesInteropOption> en tant que paramètre.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, comme son nom l’indique, implique qu’il n’existe aucune interopérabilité entre les <xref:System.EnterpriseServices> contextes et les étendues de transaction. Après création d'un objet <xref:System.Transactions.TransactionScope> avec <xref:System.Transactions.EnterpriseServicesInteropOption.None>, les modifications apportées à <xref:System.Transactions.Transaction.Current%2A> ne sont pas répercutées dans le contexte COM+. De la même façon, les modifications apportées à la transaction du contexte COM+ ne sont pas répercutées dans <xref:System.Transactions.Transaction.Current%2A>. Il s'agit du mode de fonctionnement le plus rapide pour <xref:System.Transactions>, car il n'existe aucune synchronisation supplémentaire. <xref:System.Transactions.EnterpriseServicesInteropOption.None> est la valeur par défaut utilisée par <xref:System.Transactions.TransactionScope> avec tous les constructeurs qui n'acceptent pas <xref:System.Transactions.EnterpriseServicesInteropOption> comme paramètre.  
  
 Pour associer des transactions <xref:System.EnterpriseServices> à votre transaction ambiante, vous devez utiliser <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ou <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Ces deux valeurs reposent sur une fonctionnalité appelée services sans composants, vous devez donc utiliser Windows XP Service Pack 2 ou Windows Server 2003 lors de leur exploitation.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> précise que les transactions ambiantes pour <xref:System.Transactions> et <xref:System.EnterpriseServices> sont toujours identiques. Il en résulte la création d'un nouveau contexte transactionnel <xref:System.EnterpriseServices> et l'application de la transaction en cours pour que <xref:System.Transactions.TransactionScope> soit en cours pour ce contexte. Ainsi la transaction dans <xref:System.Transactions.Transaction.Current%2A> est entièrement synchronisée avec la transaction dans <xref:System.EnterpriseServices.ContextUtil.Transaction%2A>. Cette valeur introduit une pénalité de performance car il peut s'avérer nécessaire de créer de nouveaux contextes COM+.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> spécifie les spécifications suivantes :  
  
- Si <xref:System.Transactions.Transaction.Current%2A> est activé, <xref:System.Transactions> doit prendre en charge les transactions dans le contexte COM+ s'il détecte une exécution dans un contexte autre que le contexte par défaut. Notez que le contexte par défaut ne peut pas contenir de transaction. Par conséquent, dans le contexte par défaut, même avec <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, la transaction conservée dans le stockage local des threads utilisé par <xref:System.Transactions> est retournée pour <xref:System.Transactions.Transaction.Current%2A>.  
  
- Si un nouvel objet <xref:System.Transactions.TransactionScope> est créé dans un contexte autre que celui par défaut, la transaction en cours pour l'objet <xref:System.Transactions.TransactionScope> doit être répercutée dans COM+. Dans ce cas, <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> se comporte comme <xref:System.Transactions.EnterpriseServicesInteropOption.Full> et crée donc un nouveau contexte COM+.  
  
 De plus, si <xref:System.Transactions.Transaction.Current%2A> a les valeurs <xref:System.Transactions.EnterpriseServicesInteropOption.Full> et <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, ces deux modes impliquent que <xref:System.Transactions.Transaction.Current%2A> ne peut pas être défini directement.  Toute tentative pour définir <xref:System.Transactions.Transaction.Current%2A> directement sans créer de <xref:System.Transactions.TransactionScope> entraîne une exception <xref:System.InvalidOperationException>. La valeur d'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> est héritée par de nouvelles étendues de transaction qui ne spécifient pas explicitement quelle valeur utiliser. Par exemple, si vous créez un objet <xref:System.Transactions.TransactionScope> avec la valeur <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, puis un second objet <xref:System.Transactions.TransactionScope> sans spécifier de valeur <xref:System.Transactions.EnterpriseServicesInteropOption>, cet objet <xref:System.Transactions.TransactionScope> prend également la valeur <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 En résumé, les règles suivantes s'appliquent lors de la création d'une nouvelle étendue de transaction :  
  
1. <xref:System.Transactions.Transaction.Current%2A> est vérifié pour voir s’il existe une transaction. Cette vérification entraîne :  
  
    - la recherche d'une étendue éventuelle.  
  
    - Si une étendue est détectée, la valeur de l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> passée lors de la création initiale de l'étendue est contrôlée.  
  
    - Si l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> a la valeur <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, la transaction COM+ (transaction <xref:System.EnterpriseServices>) est prioritaire sur la transaction <xref:System.Transactions> du stockage local des threads managés.  
  
         Si elle a la valeur <xref:System.Transactions.EnterpriseServicesInteropOption.None>, c'est la transaction <xref:System.Transactions> du stockage local des threads managés qui est prioritaire.  
  
         Si la valeur est <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, il n'y a qu'une transaction et il s'agit obligatoirement d'une transaction COM+.  
  
2. La valeur de l'énumération <xref:System.Transactions.TransactionScopeOption> passée par le constructeur <xref:System.Transactions.TransactionScope> est contrôlée. Cela détermine la nécessité de la création d'une nouvelle transaction.  
  
3. S'il est nécessaire de créer une nouvelle transaction, les valeurs suivantes de <xref:System.Transactions.EnterpriseServicesInteropOption> sont :  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Full> : une transaction associée à un contexte COM+ est créée.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.None>: une <xref:System.Transactions> transaction est créée.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: s’il existe un contexte COM+, une transaction est créée et attachée au contexte.  
  
 Le tableau suivant présente le contexte Enterprise Services (ES) ainsi que l'étendue transactionnelle qui requiert une transaction utilisant l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
|Contexte ES|None|Automatique|Complète|  
|----------------|----------|---------------|----------|  
|Contexte par défaut|Contexte par défaut|Contexte par défaut|Création <br />contexte transactionnel|  
|Contexte autre que celui par défaut|Conserver le contexte du client|Créer un contexte transactionnel|Créer un contexte transactionnel|  
  
 Le tableau suivant indique la transaction ambiante, selon un contexte <xref:System.EnterpriseServices> particulier et une étendue transactionnelle qui requiert une transaction utilisant l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
|Contexte ES|None|Automatique|Complète|  
|----------------|----------|---------------|----------|  
|Contexte par défaut|ST|ST|ES|  
|Contexte autre que celui par défaut|ST|ES|ES|  
  
 Dans le tableau précédent :  
  
- ST signifie que la transaction ambiante de l'étendue est managée par <xref:System.Transactions>, indépendamment de l'éventuelle présence de transactions du contexte <xref:System.EnterpriseServices>.  
  
- ES signifie que la transaction ambiante de l'étendue est identique à la transaction du contexte <xref:System.EnterpriseServices>.
