---
title: Intégration de XML aux données relationnelles et à ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
ms.openlocfilehash: 30b788c77a2352d0d02ee772ab3f428381facd9f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155618"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Intégration de XML aux données relationnelles et à ADO.NET
LaLa classe **XmlDataDocument** est une classe dérivée de **XmlDocument** et contient des données XML. L'avantage de **XmlDataDocument** est de fournir une passerelle entre les données relationnelles et hiérarchiques. Il s’agit d’un **XmlDocument** qui peut être lié à un **DataSet** et les deux classes peuvent synchroniser des changements apportés aux données contenues dans ces deux classes. Un **XmlDocument** lié à un **DataSet** permet à du XML de s'intégrer à des données relationnelles, et il n'est pas nécessaire que vos données soient représentées soit sous la forme XML, soit dans un format relationnel. Vous pouvez effectuer les deux sans être limité à une représentation unique des données.  
  
 Les avantages d'avoir les données disponibles sous deux vues sont les suivants :  
  
- La portion structurée d'un document XML peut être mappée à un groupe de données et peut être stockée, indexée et recherchée efficacement.  
  
- Transformations, validation et navigation peuvent s’effectuer de manière efficace par l’intermédiaire d’un modèle de curseur sur les données XML stockées de manière relationnelle. Il est parfois possible d'effectuer cette opération plus efficacement par rapport à des structures relationnelles que lorsque le XML est stocké dans un modèle **XmlDocument**.  
  
- Le **DataSet** peut stocker une portion du XML. Vous pouvez donc utiliser**XPath** ou **XslTransform** pour ne stocker dans un **DataSet** que les éléments et attributs présentant un intérêt. À partir de là, il est possible d'apporter des changements au sous-ensemble, plus petit et filtré, des données, les changements se propageant aux données plus volumineuses dans **XmlDataDocument**.  
  
 Vous pouvez également effectuer une transformation sur des données chargées dans le**DataSet** à partir de SQL Server. Une autre option consiste à lier des contrôles WebForm et WinForm managés par style de classes .NET Framework à un **DataSet** qui a été rempli à partir d'un flux d'entrée XML.  
  
 En plus de prendre en charge **XslTransform**, un **XmlDataDocument** expose des données relationnelles à des requêtes et validation **XPath**.  Autrement dit, tous les services XML sont disponibles pour les données relationnelles, et les fonctionnalités relationnelles, comme la liaison de contrôle, codegen, etc., sont disponibles sur une projection structurée de XML sans compromettre la fidélité du XML.  
  
 Comme **XmlDataDocument** est hérité à partir d'un **XmlDocument**, il fournit une implémentation du DOM W3C. Le fait que **XmlDataDocument** soit associé à un sous-ensemble de ses données et les stocke dans un **DataSet** ne restreint ni ne modifie en aucune manière+ son utilisation en tant que **XmlDocument**. Le code écrit pour consommer un **XmlDocument** fonctionne sans altération par rapport à un **XmlDataDocument**. Le **DataSet** fournit la vue relationnelle des mêmes données en définissant des tableaux, des colonnes, des relations et des contraintes, et correspond à un magasin autonome de données utilisateur en mémoire.  
  
 L’illustration suivante montre les différentes associations entre, d’une part, les données XML et, d’autre part, **DataSet** et **XmlDataDocument** :
  
 ![Diagramme illustrant les différentes associations avec le jeu de données XML.](./media/xml-integration-with-relational-data-and-adonet/xml-integration-relational-data-adodotnet.gif)  
  
 L'illustration montre que des données XML peuvent être chargées directement dans un **DataSet**, ce qui permet une manipulation directe avec du XML de manière relationnelle. Ou bien, le XML peut être chargé dans une classe dérivée du DOM, qui correspond au **XmlDataDocument**, puis être chargé et synchronisé avec le **DataSet**. Comme **DataSet** et **XmlDataDocument** sont synchronisés sur un seul jeu de données, des modifications apportées aux données dans un magasin sont reflétées dans l’autre magasin.  
  
 Le **XmlDataDocument** hérite de toutes les fonctionnalités de modification et de navigation à partir de **XmlDocument**. Il existe des cas où l’utilisation de **XmlDataDocument** et de ses fonctionnalités héritées, synchronisées avec un **DataSet**, représente une option plus appropriée que le chargement de XML directement dans le **DataSet**. Le tableau suivant illustre les éléments à prendre en compte lors du choix de la méthode à utiliser pour charger le **DataSet**.  
  
|Exemple de chargement du XML directement dans un DataSet|Exemple de synchronisation d’un DataSet avec un XmlDataDocument|  
|----------------------------------------------|-----------------------------------------------------------|  
|Les requêtes de données dans le **DataSet** sont plus simples avec SQL qu’avec XPath.|Les requêtes XPath sont nécessaires sur les données dans le **DataSet**.|  
|La préservation de l'ordre des éléments dans le XML source n'est pas critique.|La préservation de l'ordre des éléments dans le XML source est critique.|  
|Il n'est pas nécessaire de préserver l'espace blanc entre des éléments et la mise en forme dans le XML source.|La préservation des espaces blancs et de la mise en forme dans le XML source est critique.|  
  
 Si le chargement et l'écriture de XML directement dans un et à partir d’un **DataSet** répond à vos besoins, voir [Chargement d'un DataSet à partir de XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) et [Écriture d'un DataSet sous forme de données XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Si le chargement du **DataSet** à partir d’un **XmlDataDocument** répond à vos besoins, consultez [Synchronisation d’un DataSet avec un document XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
