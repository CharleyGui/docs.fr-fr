---
title: Procédure standard d'utilisation de LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: c7964c821a838e027302cddce704d86cc6a34f66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792343"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Procédure standard d'utilisation de LINQ to SQL
Pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], suivez les étapes décrites ultérieurement dans cette rubrique. Notez que de nombreuses étapes sont facultatives. Il est tout à fait possible que votre modèle objet soit utilisable dans son état par défaut.  
  
 Pour un démarrage très rapide, utilisez la Concepteur Objet Relationnel pour créer votre modèle objet et commencez à coder vos requêtes.  
  
## <a name="creating-the-object-model"></a>Création du modèle objet  
 La première étape consiste à créer un modèle objet à partir des métadonnées d'une base de données relationnelle existante. Le modèle objet représente la base de données en fonction du langage de programmation du développeur. Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Sélectionnez un outil pour créer le modèle.  
 Trois outils sont disponibles pour la création du modèle.  
  
- Concepteur Objet Relationnel  
  
     Ce concepteur fournit une interface utilisateur élaborée pour créer un modèle objet à partir d'une base de données existante. Cet outil fait partie de l’IDE de Visual Studio et est mieux adapté aux bases de données de taille réduite ou moyenne.  
  
- Outil de génération de code SQLMetal  
  
     Cet utilitaire de ligne de commande offre un ensemble d’options légèrement différent du Concepteur O/R. Il est mieux adapté à la modélisation de grandes bases de données. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
- Éditeur de code  
  
     Vous pouvez écrire votre propre code à l’aide de l’éditeur de code Visual Studio ou d’un autre éditeur. Nous déconseillons cette approche, qui peut être sujette à des erreurs, lorsque vous disposez d’une base de données existante et que vous pouvez utiliser le Concepteur O/R ou l’outil SQLMetal. Toutefois, l'éditeur de code peut s'avérer particulièrement utile pour affiner ou modifier du code déjà généré à l'aide d'autres outils. Pour plus d'informations, voir [Procédure : Personnaliser les classes d’entité à l’aide](how-to-customize-entity-classes-by-using-the-code-editor.md)de l’éditeur de code.  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Sélectionnez le type de code à générer.  
  
- C# Ou Visual Basic fichier de code source pour le mappage basé sur les attributs.  
  
     Vous incluez ensuite ce fichier de code dans votre projet Visual Studio. Pour plus d’informations, consultez [mappage basé sur les attributs](attribute-based-mapping.md).  
  
- Fichier XML pour le mappage externe.  
  
     Cette approche vous permet de maintenir les métadonnées de mappage en dehors de votre code d'application. Pour plus d’informations, consultez [mappage externe](external-mapping.md).  
  
    > [!NOTE]
    > Le Concepteur O/R ne prend pas en charge la génération de fichiers de mappage externes. Vous devez utiliser l'outil SQLMetal pour implémenter cette fonctionnalité.  
  
- Un fichier DBML, que vous pouvez modifier avant de générer un fichier de code final.  
  
     Il s'agit d'une fonctionnalité avancée.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Affinez le fichier de code en fonction des besoins de votre application.  
 À cet effet, vous pouvez utiliser le Concepteur O/R ou l’éditeur de code.  
  
## <a name="using-the-object-model"></a>Utilisation du modèle objet  
 L'illustration suivante montre la relation entre le développeur et les données dans un scénario à deux niveaux. Pour d’autres scénarios, consultez [applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![Capture d’écran qui montre le modèle d’objet LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Maintenant que vous disposez du modèle objet, vous pouvez décrire les demandes d'informations et manipuler des données dans ce modèle. Pensez en termes d'objets et de propriétés dans votre modèle objet et non pas en termes de lignes et de colonnes de la base de données. Vous ne traitez pas directement avec la base de données.  
  
 Lorsque vous demandez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à d’exécuter une requête que vous avez décrite ou d' `SubmitChanges()` appeler sur les données que vous avez manipulées, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communique avec la base de données dans la langue de la base de données.  
  
 La procédure standard d'utilisation du modèle objet créé est présentée ci-dessous.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Créez des requêtes pour récupérer des informations de la base de données.  
 Pour plus d’informations, consultez [concepts de requête](query-concepts.md) et exemples de [requêtes](query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Substituez des comportements par défaut pour l'insertion, la mise à jour et la suppression.  
 Cette étape est facultative. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Définissez les options appropriées pour détecter et signaler des conflits d'accès concurrentiel.  
 Vous pouvez conserver les valeurs par défaut de votre modèle pour la gestion des conflits d'accès concurrentiel ou les adapter à vos besoins. Pour plus d’informations, consultez [Guide pratique pour Spécifiez les membres qui sont testés pour](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) les [conflits d’accès concurrentiel et comment : Spécifiez le moment où des exceptions](how-to-specify-when-concurrency-exceptions-are-thrown.md)d’accès concurrentiel sont levées.  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Établissez une hiérarchie d'héritage.  
 Cette étape est facultative. Pour plus d’informations, consultez [prise en charge de l’héritage](inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Fournissez une interface utilisateur appropriée.  
 Cette étape est facultative et dépend de l'utilisation ultérieure de votre application.  
  
### <a name="6-debug-and-test-your-application"></a>6. Déboguez et testez votre application.  
 Pour plus d’informations, consultez [prise en charge du débogage](debugging-support.md).  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started.md)
- [Création du modèle objet](creating-the-object-model.md)
- [Procédures stockées](stored-procedures.md)
