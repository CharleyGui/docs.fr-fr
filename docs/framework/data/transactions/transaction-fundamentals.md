---
title: Notions de base des transactions
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: ed5865121a32f05f9b58c0ca0fca475fe7b98723
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346217"
---
# <a name="transaction-fundamentals"></a>Notions de base des transactions
Les transactions servent à lier plusieurs tâches ensemble. Par exemple, imaginez qu'une application effectue deux tâches. Une table est d'abord créée dans une base de données. Un objet spécialisé est ensuite appelé pour collecter, formater et insérer des données dans la nouvelle table. Ces deux tâches sont liées et sont même interdépendantes. Cela vous évite de créer une nouvelle table sauf si vous devez y insérer des données. L'exécution des deux tâches au sein de l'étendue d'une seule transaction effectue la connexion entre les deux. Si la seconde tâche échoue, la première est restaurée à un point intervenant avant la création de la nouvelle table.  
  
 Pour garantir un comportement prévisible, toutes les transactions doivent posséder les propriétés ACID de base (atomicité, cohérence, isolation et durabilité). Ces propriétés renforcent le rôle des transactions fondamentales en tant que propositions tout-ou-rien. Pour plus d’informations sur ACID, consultez [propriétés ACID](/windows/win32/cossdk/acid-properties). En résumé, les propriétés ACID garantissent la réussite ou l'échec d'un ensemble de tâches en tant qu'unité. En terminologie de traitement de transaction, une transaction est validée ou abandonnée. Pour qu'une transaction soit validée, tous les participants doivent s'assurer que chaque modification apportée aux données est permanente. Ces modifications doivent persister même en cas de panne du système ou de tout autre événement imprévu. Si l'un des participants seulement ne respecte pas cette garantie, l'intégralité de la transaction échoue. Toutes les modifications apportées aux données au sein de l'étendue de la transaction sont restaurées à un point spécifique.  
  
 Une transaction peut être restreinte à une seule ressource de données, telle qu'une base de données ou une file d'attente de messages. Dans ce cas, la transaction locale est gérée par le gestionnaire de transactions fourni par <xref:System.Transactions>, qui permet de générer un gain de performance. Contrôlées par la ressource de données, ces transactions sont efficaces et faciles à gérer.  
  
 Les transactions peuvent également couvrir plusieurs ressources de données. Les transactions distribuées permettent d'intégrer plusieurs opérations se produisant sur différents systèmes en une seule action de réussite ou d'échec. Dans ce cas, les transactions sont coordonnées par le MSDTC (Microsoft Distributed Transaction Coordinator) de chaque système.  
  
 Lors du développement d'une application transactionnelle à l'aide des classes fournies par <xref:System.Transactions>, il n'est pas nécessaire de s'interroger sur le type de transaction requise ou sur le gestionnaire de transactions concerné. L'infrastructure <xref:System.Transactions> gère automatiquement ces questions pour vous.  
  
 Lorsque vous créez une transaction, vous pouvez spécifier le niveau d'isolation qui s'y applique. Le niveau d’isolation, défini par l’énumération <xref:System.Transactions.IsolationLevel>, détermine le niveau d’accès d’autres transactions aux données affectées par votre transaction.  
  
 Vous pouvez créer des transactions à l’aide de ADO.NET, <xref:System.EnterpriseServices>ou du modèle de programmation transactionnelle fourni par l’espace de noms <xref:System.Transactions>. La rubrique [fonctionnalités fournies par System. transactions](features-provided-by-system-transactions.md) traite des fonctionnalités que vous pouvez utiliser pour écrire une application transactionnelle à l’aide de l’espace de noms <xref:System.Transactions>.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités fournies par System.Transactions](features-provided-by-system-transactions.md)
