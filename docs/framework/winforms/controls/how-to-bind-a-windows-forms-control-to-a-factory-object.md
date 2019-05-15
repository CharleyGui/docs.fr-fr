---
title: 'Procédure : lier un contrôle Windows Forms à un objet de fabrique'
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
ms.openlocfilehash: b64545528746e50d00f88d626a07ac98839e926c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589734"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Procédure : lier un contrôle Windows Forms à un objet de fabrique
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
- [Guide pratique pour Lier un contrôle de formulaires Windows à un Type](how-to-bind-a-windows-forms-control-to-a-type.md)
