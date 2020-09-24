---
title: 'Procédure pas à pas : Interrogation entre relations (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: ce5323b4ecd7bd0c4337d4632eff209e4d0ebd42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163984"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Procédure pas à pas : Interrogation entre relations (Visual Basic)

Cette procédure pas à pas montre comment utiliser des [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* pour représenter les relations de clé étrangère dans la base de données.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.  
  
## <a name="prerequisites"></a>Prérequis  

 Vous devez avoir terminé la [procédure pas à pas : requête et modèle objet simples (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md). Cette procédure pas à pas est basée sur cette dernière, y compris la présence du fichier northwnd.mdf dans c:\linqtest.  
  
## <a name="overview"></a>Vue d’ensemble  

 Cette procédure pas à pas se compose de trois tâches principales :  
  
- Ajout d'une classe d'entité pour représenter la table Orders dans l'exemple de base de données Northwind.  
  
- Ajout d'annotations à la classe `Customer` pour améliorer la relation entre les classes `Customer` et `Order`.  
  
- Création et exécution d'une requête pour essayer d'obtenir des informations `Order` en utilisant la classe `Customer`.  
  
## <a name="mapping-relationships-across-tables"></a>Mappage de relations entre des tables  

 Une fois la définition de classe `Customer` terminée, créez la définition de classe d'entité `Order` qui inclut le code suivant indiquant que `Orders.Customer` est une clé étrangère de `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Pour ajouter la classe d'entité Order  
  
- Tapez ou collez le code suivant après la classe `Customer` :  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Annotation de la classe Customer  

 Dans cette étape, annotez la classe `Customer` pour indiquer sa relation avec la classe `Order`. Cet ajout n'est pas strictement nécessaire étant donné que la définition de la relation dans chacune des directions est suffisante pour créer le lien. Cependant, l'ajout de cette annotation vous permet de naviguer facilement parmi les objets dans chacune des directions.  
  
#### <a name="to-annotate-the-customer-class"></a>Pour annoter la classe Customer  
  
- Tapez ou collez le code suivant dans la classe `Customer` :  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Création et exécution d'une requête dans la relation entre les classes Order et Customer  

 Vous pouvez désormais accéder aux objets `Order` directement à partir des objets `Customer` ou inversement. Vous n’avez pas besoin d’une *jointure* explicite entre les clients et les commandes.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Pour accéder aux objets Order à l'aide d'objets Customer  
  
1. Modifiez la méthode `Sub Main` en tapant ou en collant le code suivant dans la méthode :  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Appuyez sur F5 pour déboguer l'application.  
  
     Deux noms apparaissent dans le message et la fenêtre de console affiche le code SQL généré.  
  
3. Fermez le message pour arrêter le débogage.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Création d'une vue fortement typée de votre base de données  

 Il est beaucoup plus facile de démarrer avec une vue fortement typée de votre base de données. En effectuant un typage fort de l'objet <xref:System.Data.Linq.DataContext>, vous n'avez pas besoin d'effectuer des appels à <xref:System.Data.Linq.DataContext.GetTable%2A>. Vous pouvez utiliser des tables fortement typées dans toutes vos requêtes lorsque vous utilisez l'objet <xref:System.Data.Linq.DataContext> fortement typé.  
  
 Dans les étapes suivantes, vous créerez `Customers` comme table fortement typée qui mappe à la table Customers dans la base de données.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Pour effectuer un typage fort de l'objet DataContext  
  
1. Ajoutez le code suivant au-dessus de la déclaration de classe `Customer`.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Modifiez `Sub Main` pour utiliser le <xref:System.Data.Linq.DataContext> fortement typé comme suit :  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Appuyez sur F5 pour déboguer l'application.  
  
     La sortie de la fenêtre de console est :  
  
     `ID=WHITC`  
  
4. Appuyez sur Entrée dans la fenêtre de console pour fermer l'application.  
  
5. Dans le menu **fichier** , cliquez sur **enregistrer tout** si vous souhaitez enregistrer cette application.  
  
## <a name="next-steps"></a>Étapes suivantes  

 La procédure pas à pas suivante ([procédure pas à pas : manipulation de données (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) montre comment manipuler les données. Cette procédure pas à pas ne requiert pas d'enregistrer les deux procédures pas à pas de cette série que vous avez déjà terminées.  
  
## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
