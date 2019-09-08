---
title: Vue d'ensemble du modèle Factory
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 7d50ddd3b02b66a5b2be41eaba5cf9a497b5f1b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795087"
---
# <a name="factory-model-overview"></a>Vue d'ensemble du modèle Factory
ADO.NET 2.0 a introduit de nouvelles classes de base dans l'espace de noms <xref:System.Data.Common>. Les classes de base sont abstraites, ce qui signifie qu'elles ne peuvent pas être directement instanciées. Il s'agit des classes <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbDataAdapter> qui sont en outre partagées par les fournisseurs de données .NET Framework, tels que <xref:System.Data.SqlClient> et <xref:System.Data.OleDb>. L'introduction de classes de base simplifie l'ajout de fonctionnalités aux fournisseurs de données .NET Framework sans avoir recours à la création de nouvelles interfaces.  
  
 ADO.NET 2.0 a également introduit des classes de base abstraites pour permettre aux développeurs d'écrire du code générique d'accès aux données qui ne dépend pas d'un fournisseur de données spécifique.  
  
## <a name="the-factory-design-pattern"></a>Modèle de design Factory  
 Le modèle de programmation permettant d'écrire du code indépendant du fournisseur repose sur l'utilisation du modèle de design « Factory ». Ce modèle utilise une seule API pour accéder à des bases de données sur plusieurs fournisseurs. Ce modèle est correctement nommé, puisqu’il invoque l’utilisation d’un objet spécialisé uniquement pour créer d’autres objets, un peu comme un véritable factory. Pour obtenir une description plus détaillée du modèle de conception Factory, consultez [écriture de code générique d’accès aux données dans ASP.NET 2,0 et ADO.NET 2,0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 À partir d'ADO.NET 2.0, la classe <xref:System.Data.Common.DbProviderFactories> fournit des méthodes `static` (ou `Shared` en Visual Basic) pour créer une instance <xref:System.Data.Common.DbProviderFactory>. Cette instance retourne ensuite un objet fortement typé correct reposant sur les informations du fournisseur et la chaîne de connexion fournie au moment de l'exécution.  
  
## <a name="see-also"></a>Voir aussi

- [Obtention d’un DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand et DbException](dbconnection-dbcommand-and-dbexception.md)
- [Modification des données avec un DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
