---
title: Apprentissage par les procédures pas à pas
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: e6b5f77d6d918ae1402074c9c3037ccadec8ac02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743032"
---
# <a name="learning-by-walkthroughs"></a>Apprentissage par les procédures pas à pas
Le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation fournit plusieurs procédures pas à pas. Cette rubrique aborde certains problèmes généraux de procédure pas à pas (y compris leur résolution) et fournit des liens vers plusieurs procédures pas à pas de base pour découvrir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Les procédures pas à pas de cette section Mise en route vous exposent le code de base qui prend en charge la technologie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Dans la pratique, vous utiliserez généralement les projets concepteur objet/relationnel et Windows Forms pour implémenter votre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications. La documentation du Concepteur O/R fournit des exemples et procédures pas à pas à cet effet.  
  
## <a name="getting-started-walkthroughs"></a>Procédures pas à pas de mise en route  
 Plusieurs procédures pas à pas sont disponibles dans cette section. Ces procédures pas à pas sont basées sur l’exemple de base de données Northwind et présentent des fonctionnalités de complexité minimale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à un rythme abordable.  
  
 Une progression classique serait comme suit :  
  
|Objectif|Visual Basic|C#|  
|---------------|------------------|---------|  
|Créez une classe d'entité et exécutez une requête simple.|[Procédure pas à pas : Modèle objet simples et requête (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Procédure pas à pas : Requête et modèle objet simples (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Ajoutez une deuxième classe et exécutez une requête plus complexe.<br /><br /> (Requiert l'achèvement de la procédure pas à pas précédente).|[Procédure pas à pas : Interrogation de relations (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Procédure pas à pas : Interrogation de relations (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Ajoutez, modifiez et supprimez des éléments dans la base de données.|[Procédure pas à pas : Manipulation de données (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Procédure pas à pas : Manipulation de données (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Utilisez des procédures stockées.|[Procédure pas à pas : À l’aide de procédures stockées uniquement (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Procédure pas à pas : À l’aide de procédures stockées uniquement (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Généralités  
 Les informations suivantes se rapportent à ces procédures pas à pas en général :  
  
- Environnement : Chaque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] procédure pas à pas utilise Visual Studio comme environnement de développement intégré (IDE).  
  
- Moteurs SQL : Ces procédures pas à pas sont écrites pour être implémentées à l’aide de SQL Server Express. Si vous n'avez pas SQL Server Express, vous pouvez le télécharger gratuitement. Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  Les procédures pas à pas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent un nom de fichier comme chaîne de connexion. La simple spécification d'un nom de fichier est une commodité fournie par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les utilisateurs de SQL Server Express. Faites toujours attention aux problèmes de sécurité. Pour plus d’informations, consultez [sécurité dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] procédures pas à pas nécessite généralement la base de données Northwind. Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
- Les boîtes de dialogue et commandes de menu affichées dans les procédures pas à pas peuvent différer de celles décrites dans l’aide, en fonction de vos paramètres actifs ou votre édition de Visual Studio. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
- Pour les procédures pas à pas qui abordent des scénarios multicouches, un serveur doit se trouver sur un ordinateur autre que l'ordinateur de développement et vous devez disposer des autorisations appropriées pour accéder au serveur.  
  
- Le nom de la classe qui représente en général la table Orders dans l'exemple de base de données Northwind est `[Order]`. La séquence d’échappement est nécessaire car `Order` est un mot clé dans Visual Basic.  
  
## <a name="troubleshooting"></a>Résolution de problèmes  
 Des erreurs d'exécution peuvent se produire car vous ne disposez pas des autorisations suffisantes pour accéder aux bases de données utilisées dans ces procédures pas à pas. Consultez les étapes suivantes pour résoudre les problèmes les plus courants.  
  
### <a name="log-on-issues"></a>Problèmes de connexion  
 Votre application tente peut-être d'accéder à la base de données via une connexion à une base de données qu'elle n'accepte pas.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Pour vérifier ou modifier la connexion à la base de données  
  
1. Sur le Windows **Démarrer** menu, pointez sur **tous les programmes**, **Microsoft SQL Server 2005**, pointez sur **outils de Configuration**, puis cliquez sur **Gestionnaire de Configuration SQL Server**.  
  
2. Dans le volet gauche de la **Gestionnaire de Configuration SQL Server**, cliquez sur **SQL Server 2005 Services**.  
  
3. Dans le volet droit, cliquez sur **SQL Server (SQLEXPRESS)** , puis cliquez sur **propriétés**.  
  
4. Cliquez sur le **ouverture de session** onglet et vérifiez la façon dont vous tentez d’ouvrir une session sur le serveur.  
  
     Dans la plupart des cas, **système Local** fonctionne.  
  
     Si vous apportez une modification, cliquez sur **redémarrer** pour redémarrer le service.  
  
### <a name="protocols"></a>Protocoles  
 Parfois, les protocoles ne peuvent pas être définis correctement pour que votre application puisse accéder à la base de données. Par exemple, le **canaux nommés** protocole, ce qui est requis pour les procédures pas à pas dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], n’est pas activé par défaut.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Pour activer le protocole Canaux nommés  
  
1. Dans le volet gauche de la **Gestionnaire de Configuration SQL Server**, développez **Configuration du réseau SQL Server 2005**, puis cliquez sur **protocoles pour SQLEXPRESS**.  
  
2. Dans le volet droit, vérifiez que le **canaux nommés** protocole est activé. Si elle n’est pas le cas, cliquez sur **canaux nommés** puis cliquez sur **activer**.  
  
     Vous devrez arrêter et redémarrer le service. Suivez les étapes du bloc suivant.  
  
### <a name="stopping-and-restarting-the-service"></a>Arrêt et redémarrage du service  
 Vous devez arrêter et redémarrer les services pour que vos modifications soient prises en compte.  
  
##### <a name="to-stop-and-restart-the-service"></a>Pour arrêter et redémarrer le service  
  
1. Dans le volet gauche de la **Gestionnaire de Configuration SQL Server**, cliquez sur **SQL Server 2005 Services**.  
  
2. Dans le volet droit, cliquez sur **SQL Server (SQLEXPRESS)** , puis cliquez sur **arrêter**.  
  
3. Avec le bouton droit **SQL Server (SQLEXPRESS)** , puis cliquez sur **redémarrer**.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
