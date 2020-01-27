---
title: Lier le contrôle à un objet de fabrique
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745095"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Comment : lier un contrôle Windows Forms à un objet Factory
Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un objet ou à une méthode qui génère d'autres objets. Un tel objet ou une telle méthode porte le nom de fabrique. Votre source de données peut par exemple être la valeur de retour d'un appel de méthode, plutôt qu'un objet en mémoire ou un type. Vous pouvez lier un contrôle à ce genre de source de données tant que la source retourne une collection.  
  
 Vous pouvez facilement lier un contrôle à un objet de fabrique à l'aide du contrôle <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à une méthode de fabrique à l'aide d'un contrôle <xref:System.Windows.Forms.BindingSource>. La méthode de fabrique se nomme `GetOrdersByCustomerId` et retourne toutes les commandes pour un client donné dans la base de données Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, composant](bindingsource-component.md)
- [Comment : lier un contrôle Windows Forms à un type](how-to-bind-a-windows-forms-control-to-a-type.md)
