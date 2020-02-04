---
title: Exécution côte à côte
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: a624aac2ed1f3ab124973c84bc74e39297600c8b
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980013"
---
# <a name="side-by-side-execution-in-adonet"></a>Exécution côte à côte dans ADO.NET
L’exécution côte à côte dans le .NET Framework est la possibilité d’exécuter une application sur un ordinateur sur lequel plusieurs versions du .NET Framework installées, en utilisant exclusivement la version pour laquelle l’application a été compilée. Pour plus d’informations sur la configuration de l’exécution côte à côte, consultez [exécution côte à côte](../../deployment/side-by-side-execution.md).  
  
 Une application compilée à l’aide d’une version de l' .NET Framework peut s’exécuter sur une version différente du .NET Framework. Toutefois, nous vous recommandons de compiler une version de l’application pour chaque version installée du .NET Framework et de les exécuter séparément. Dans les deux cas, vous devez être conscient des modifications apportées à ADO.NET entre les mises en production qui peuvent affecter la compatibilité ascendante ou la compatibilité descendante de votre application.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Compatibilités descendante et ascendante  
 La compatibilité ascendante signifie qu’une application peut être compilée avec une version antérieure du .NET Framework, mais s’exécutera toujours avec succès sur une version ultérieure du .NET Framework. Le code ADO.NET écrit pour la version 1,1 de .NET Framework est compatible en amont avec les versions ultérieures.  
  
 La compatibilité descendante signifie qu’une application est compilée pour une version plus récente du .NET Framework, mais continue à s’exécuter sur des versions antérieures du .NET Framework sans aucune perte de fonctionnalité. Bien entendu, ce n’est pas le cas pour les fonctionnalités introduites dans une nouvelle version du .NET Framework.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Fournisseur de données .NET Framework pour ODBC  
 À partir de la version 1,1, la .NET Framework Fournisseur de données pour ODBC (<xref:System.Data.Odbc>) est incluse dans le cadre de la .NET Framework.
  
 Si vous disposez d’une application développée pour la version .NET Framework 1,0 qui utilise le fournisseur de données ODBC pour se connecter à votre source de données, et que vous souhaitez exécuter cette application sur la version .NET Framework 1,1 ou une version ultérieure, vous devez mettre à jour l’espace de noms du fournisseur de données ODBC vers **System. Data. ODBC**. Vous devez ensuite le recompiler pour la version plus récente du .NET Framework.  
  
 Si vous avez une application développée pour la .NET Framework version 2,0 ou ultérieure qui utilise le fournisseur de données ODBC pour se connecter à votre source de données et que vous souhaitez exécuter cette application sur la version .NET Framework 1,0, vous devez télécharger le fournisseur de données ODBC et l’installer. sur le système .NET Framework version 1,0. Vous devez ensuite remplacer l’espace de noms du fournisseur de données ODBC par **Microsoft. Data. ODBC**et recompiler l’application pour le .NET Framework version 1,0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Fournisseur de données .NET Framework pour Oracle  
 À partir de la version 1,1, la .NET Framework Fournisseur de données pour Oracle (<xref:System.Data.OracleClient>) est incluse dans le cadre de la .NET Framework.
  
 Si vous avez une application développée pour la .NET Framework version 2,0 ou ultérieure qui utilise le fournisseur de données pour se connecter à votre source de données, et que vous souhaitez exécuter cette application sur la version .NET Framework 1,0, vous devez télécharger le fournisseur de données et l’installer sur le. Système T Framework version 1,0.  
  
## <a name="code-access-security"></a>Sécurité d'accès du code  
 Les fournisseurs de données .NET Framework dans la .NET Framework version 1,0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) doivent être exécutés avec l’autorisation FullTrust. Toute tentative d’utilisation des fournisseurs de données .NET Framework k à partir de la version .NET Framework 1,0 dans une zone avec une autorisation inférieure à FullTrust entraîne une <xref:System.Security.SecurityException>.  
  
 Toutefois, à partir de la version 2,0 de .NET Framework, tous les fournisseurs de données .NET Framework peuvent être utilisés dans des zones de confiance partielle. En outre, une nouvelle fonctionnalité de sécurité a été ajoutée aux fournisseurs de données .NET Framework dans le .NET Framework version 1,1. Cette fonctionnalité vous permet de restreindre les chaînes de connexion qui peuvent être utilisées dans une zone de sécurité particulière. Vous pouvez également désactiver l'utilisation des mots de passe vides pour une zone de sécurité particulière. Pour plus d'informations, consultez [Code Access Security and ADO.NET](code-access-security.md).  
  
 Étant donné que chaque installation du .NET Framework a un fichier Security. config distinct, il n’existe aucun problème de compatibilité avec les paramètres de sécurité. Toutefois, si votre application dépend des fonctionnalités de sécurité supplémentaires de ADO.NET incluses dans le .NET Framework version 1,1 et versions ultérieures, vous ne pourrez pas la distribuer à un système version 1,0.  
  
## <a name="sqlcommand-execution"></a>Exécution de SqlCommand  
 À partir de la version 1,1 de .NET Framework, la façon dont <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> exécute les commandes au niveau de la source de données a été modifiée.  
  
 Dans la version 1,0 de .NET Framework, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> exécuté toutes les commandes dans le contexte de la procédure stockée **sp_executesql** . Par conséquent, les commandes qui affectent l'état de la connexion (SET NOCOUNT ON, par exemple) ne s'appliquent qu'à l'exécution de la commande actuelle. L'état de la connexion n'est pas modifié pour les commandes suivantes qui sont exécutées pendant que la connexion est ouverte.  
  
 Dans le .NET Framework version 1,1 et versions ultérieures, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> exécute uniquement une commande dans le contexte de la procédure stockée **sp_executesql** si la commande contient des paramètres, ce qui offre un avantage en matière de performances. Par conséquent, si une commande affectant l'état de la connexion est incluse dans une commande non paramétrée, elle modifie l'état de la connexion pour toutes les commandes suivantes exécutées pendant que la connexion est ouverte.  
  
 Considérez le lot de commandes suivant exécuté dans un appel à <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 Dans le .NET Framework version 1,1 et versions ultérieures, NOCOUNT reste activé pour toutes les commandes suivantes exécutées pendant que la connexion est ouverte. Dans la version .NET Framework 1,0, NOCOUNT est activé uniquement pour l’exécution de la commande actuelle.  
  
 Cette modification peut affecter la compatibilité ascendante et descendante de votre application si vous dépendez du comportement de <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pour les deux versions du .NET Framework.  
  
 Pour les applications qui s’exécutent à la fois sur les versions antérieures et ultérieures du .NET Framework, vous pouvez écrire votre code pour vous assurer que le comportement est le même quelle que soit la version que vous exécutez. Si vous souhaitez vous assurer qu'une commande modifie l'état de la connexion pour toutes les commandes suivantes, nous vous recommandons d'exécuter votre commande à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Si vous souhaitez vous assurer qu'une commande ne modifie pas la connexion pour toutes les commandes suivantes, nous vous recommandons d'inclure les commandes qui rétablissent l'état de la connexion dans votre commande. Par exemple :  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
