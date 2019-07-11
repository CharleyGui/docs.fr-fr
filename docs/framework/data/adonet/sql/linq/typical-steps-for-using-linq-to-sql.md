---
title: Procédure standard d'utilisation de LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: cbcd8099fd085d0198e5ba77ee0a3e86c1ca70d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742769"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Procédure standard d'utilisation de LINQ to SQL
Pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], suivez les étapes décrites ultérieurement dans cette rubrique. Notez que de nombreuses étapes sont facultatives. Il est tout à fait possible que votre modèle objet soit utilisable dans son état par défaut.  
  
 Pour un démarrage rapide, utilisez le concepteur objet/relationnel pour créer votre modèle objet et commencez à coder vos requêtes.  
  
## <a name="creating-the-object-model"></a>Création du modèle objet  
 La première étape consiste à créer un modèle objet à partir des métadonnées d'une base de données relationnelle existante. Le modèle objet représente la base de données en fonction du langage de programmation du développeur. Pour plus d’informations, consultez [le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Sélectionnez un outil pour créer le modèle.  
 Trois outils sont disponibles pour la création du modèle.  
  
- Le concepteur objet/relationnel  
  
     Ce concepteur fournit une interface utilisateur élaborée pour créer un modèle objet à partir d'une base de données existante. Cet outil fait partie de l’IDE Visual Studio et convient mieux aux bases de données de taille réduites ou moyennes.  
  
- Outil de génération de code SQLMetal  
  
     Cet utilitaire de ligne de commande fournit un ensemble d’options légèrement différent à partir du Concepteur O/R. Il est mieux adapté à la modélisation de grandes bases de données. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
- Éditeur de code  
  
     Vous pouvez écrire votre propre code à l’aide de l’éditeur de code Visual Studio ou un autre éditeur. Nous ne recommandons pas cette approche, ce qui peut être sujette aux erreurs, lorsque vous avez une base de données existante et que vous pouvez utiliser l’outil SQLMetal ou le Concepteur O/R. Toutefois, l'éditeur de code peut s'avérer particulièrement utile pour affiner ou modifier du code déjà généré à l'aide d'autres outils. Pour plus d’informations, consultez [Guide pratique pour Personnaliser des Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Sélectionnez le type de code à générer.  
  
- Un C# ou fichier de code source Visual Basic pour le mappage basé sur l’attribut.  
  
     Vous incluez ensuite ce fichier de code dans votre projet Visual Studio. Pour plus d’informations, consultez [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Fichier XML pour le mappage externe.  
  
     Cette approche vous permet de maintenir les métadonnées de mappage en dehors de votre code d'application. Pour plus d’informations, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  Le Concepteur O/R ne prend pas en charge la génération de fichiers de mappage externe. Vous devez utiliser l'outil SQLMetal pour implémenter cette fonctionnalité.  
  
- Un fichier DBML, que vous pouvez modifier avant de générer un fichier de code final.  
  
     Il s'agit d'une fonctionnalité avancée.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Affinez le fichier de code en fonction des besoins de votre application.  
 Pour cela, vous pouvez utiliser le Concepteur O/R ou l’éditeur de code.  
  
## <a name="using-the-object-model"></a>Utilisation du modèle objet  
 L'illustration suivante montre la relation entre le développeur et les données dans un scénario à deux niveaux. Pour d’autres scénarios, consultez [multicouches et des Applications distantes avec LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![Capture d’écran montre le modèle d’objet Linq.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Maintenant que vous disposez du modèle objet, vous pouvez décrire les demandes d'informations et manipuler des données dans ce modèle. Pensez en termes d'objets et de propriétés dans votre modèle objet et non pas en termes de lignes et de colonnes de la base de données. Vous ne traitez pas directement avec la base de données.  
  
 Lorsque vous indiquez à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] d’exécuter une requête que vous avez décrite ou un appel `SubmitChanges()` sur les données que vous avez manipulées, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communique avec la base de données dans la langue de la base de données.  
  
 La procédure standard d'utilisation du modèle objet créé est présentée ci-dessous.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Créez des requêtes pour récupérer des informations de la base de données.  
 Pour plus d’informations, consultez [concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) et [exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Substituez des comportements par défaut pour l'insertion, la mise à jour et la suppression.  
 Cette étape est facultative. Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Définissez les options appropriées pour détecter et signaler des conflits d'accès concurrentiel.  
 Vous pouvez conserver les valeurs par défaut de votre modèle pour la gestion des conflits d'accès concurrentiel ou les adapter à vos besoins. Pour plus d’informations, consultez [Guide pratique pour Spécifier les membres sont vérifiés pour les conflits d’accès concurrentiel](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) et [Comment : Spécifiez quand les Exceptions d’accès concurrentiel sont levées](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Établissez une hiérarchie d'héritage.  
 Cette étape est facultative. Pour plus d’informations, consultez [prise en charge l’héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Fournissez une interface utilisateur appropriée.  
 Cette étape est facultative et dépend de l'utilisation ultérieure de votre application.  
  
### <a name="6-debug-and-test-your-application"></a>6. Déboguez et testez votre application.  
 Pour plus d’informations, consultez [prise en charge de débogage](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
