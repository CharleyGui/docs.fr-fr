---
title: Applications multicouches LINQ to SQL avec les services Web
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 2a6e7cb177d475802d4516d6a7a91f9f5687eada
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555872"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>Applications multicouches LINQ to SQL avec les services Web
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est conçu spécialement pour une utilisation sur la couche intermédiaire dans une couche d’accès aux données (DAL) faiblement couplée, comme un service Web. Si la couche Présentation est une page web ASP.NET, vous utilisez le contrôle serveur web <xref:System.Web.UI.WebControls.LinqDataSource> pour gérer le transfert de données entre l’interface utilisateur et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sur la couche intermédiaire. Si la couche de présentation n’est pas une page ASP.NET, la couche intermédiaire et la couche de présentation doivent exécuter des tâches supplémentaires pour gérer la sérialisation et la désérialisation des données.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Configuration de LINQ to SQL sur la couche intermédiaire  
 Dans un service Web ou une application multicouche, la couche intermédiaire contient le contexte des données et les classes d'entité. Vous pouvez créer ces classes manuellement, ou à l’aide de SQLMetal.exe ou de l’Concepteur Objet Relationnel, comme décrit dans la documentation. Au moment du design, vous pouvez choisir de rendre les classes d'entité sérialisables. Pour plus d’informations, consultez [Comment : rendre des entités sérialisables](how-to-make-entities-serializable.md). Une autre option consiste à créer un ensemble distinct de classes qui encapsulent les données à sérialiser, puis à projeter dans ces types sérialisables lorsque vous retournez des données dans vos requêtes LINQ.  
  
 Vous définissez ensuite l'interface avec les méthodes que les clients appelleront pour extraire, insérer et mettre à jour les données. Les méthodes d’interface encapsulent vos requêtes LINQ. Vous pouvez utiliser tout type de mécanisme de sérialisation pour gérer les appels de méthode distants et la sérialisation de données. La seule contrainte à respecter est la suivante : si votre modèle objet comporte des relations circulaires ou bidirectionnelles, comme entre Customers et Orders dans le modèle objet Northwind standard, vous devez utiliser un sérialiseur qui le prend en charge. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> prend en charge les relations bidirectionnelles, mais ce n'est pas le cas de XmlSerializer qui est utilisé avec des services Web autres que WCF. Si vous choisissez d'utiliser le XmlSerializer, vous devez vous assurer que votre modèle objet ne comporte pas de relations cycliques.  
  
 Pour plus d’informations sur la Windows Communication Foundation, consultez [Windows Communication Foundation services et WCF Data Services dans Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Implémentez vos règles métier ou toute autre logique spécifique au domaine en utilisant les classes et méthodes partielles sur <xref:System.Data.Linq.DataContext> et les classes d'entité pour le raccordement aux événements d'exécution de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Pour plus d’informations, consultez Implémentation de la [logique métier multicouche](implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Définition des types sérialisables  
 Le niveau client ou la couche Présentation doit comporter des définitions de type pour les classes qu'elle recevra de la couche intermédiaire. Ces types peuvent être les classes d'entité elles-mêmes ou des classes spéciales qui encapsulent uniquement certains champs des classes d'entité pour la communication à distance. Dans tous les cas, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est complètement sans souci quant à la façon dont la couche présentation acquiert ces définitions de type. Par exemple, la couche de présentation peut utiliser WCF pour générer les types automatiquement, ou elle peut posséder une copie d'une DLL dans laquelle ces types sont définis, ou elle peut simplement définir sa propre version des types.  
  
## <a name="retrieving-and-inserting-data"></a>Récupération et insertion de données  
 La couche intermédiaire définit une interface qui spécifie la manière dont la couche Présentation accède aux données. Par exemple, `GetProductByID(int productID)` ou `GetCustomers()`. Sur la couche intermédiaire, le corps de méthode crée en général une nouvelle instance du <xref:System.Data.Linq.DataContext>, exécute une requête sur une ou plusieurs de ses tables. La couche intermédiaire retourne ensuite le résultat sous la forme de <xref:System.Collections.Generic.IEnumerable%601>, où `T` est une classe d'entité ou un autre type utilisé pour la sérialisation. La couche Présentation n'envoie ni ne reçoit jamais directement de variables de requête vers la couche intermédiaire ou à partir de celle-ci. Les deux couches échangent des valeurs, des objets et des collections de données concrètes. Une fois qu’elle a reçu une collection, la couche présentation peut utiliser LINQ to Objects pour l’interroger si nécessaire.  
  
 Lors de l'insertion de données, la couche Présentation peut générer un nouvel objet et l'envoyer à la couche intermédiaire, ou peut donner à la couche intermédiaire l'instruction de créer l'objet d'après les valeurs qu'elle fournit. En général, la récupération et l'insertion de données dans les applications multicouches ne diffèrent pas beaucoup du processus exécuté dans les applications à deux couches. Pour plus d’informations, consultez [interrogation de la base de données](querying-the-database.md) et [création et envoi de modifications de données](making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Suivi des modifications pour les mises à jour et les suppressions  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge l'accès concurrentiel optimiste selon les horodatages (également nommés RowVersions) et les valeurs d'origine. Si les tables de base de données contiennent des horodatages, les mises à jour et les suppressions requièrent peu de tâches supplémentaires sur la couche intermédiaire et la couche Présentation. Toutefois, si vous devez utiliser des valeurs d'origine pour les contrôles d'accès concurrentiel optimiste, la couche Présentation est chargée du suivi de ces valeurs et de leur renvoi en cas de mises à jour. En effet, les modifications apportées aux entités sur la couche Présentation ne sont pas suivies sur la couche intermédiaire. En fait, la récupération initiale d'une entité et sa mise à jour éventuelle sont généralement effectuées par deux instances entièrement distinctes du <xref:System.Data.Linq.DataContext>.  
  
 Plus le nombre des modifications effectuées par la couche Présentation est élevé, plus le suivi de ces modifications et leur renvoi sur la couche intermédiaire sont complexes. L'implémentation d'un mécanisme permettant de communiquer les modifications est entièrement à la charge de l'application. La seule exigence est que les valeurs d’origine requises pour les contrôles d’accès concurrentiel optimiste doivent être fournies à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Pour plus d’informations, consultez [extraction de données et opérations CUD dans les applications multicouches (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Voir aussi

- [Applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Vue d’ensemble du contrôle serveur Web LinqDataSource](/previous-versions/aspnet/bb547113(v=vs.100))
