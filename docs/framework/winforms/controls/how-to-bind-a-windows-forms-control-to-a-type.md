---
title: Lier le contrôle à un type
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744988"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Comment : lier un contrôle Windows Forms à un type
Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un type plutôt qu'à un objet. Cette situation se présente surtout au moment du design, quand les données peuvent ne pas être disponibles mais que vos contrôles liés aux données ont quand même besoin d'afficher des informations à partir de l'interface publique d'un type. Par exemple, vous pouvez lier un contrôle <xref:System.Windows.Forms.DataGridView> à un objet exposé par un service web et vouloir que le contrôle <xref:System.Windows.Forms.DataGridView> étiquette ses colonnes au moment du design avec les noms de membres d'un type personnalisé.  
  
 Vous pouvez facilement lier un contrôle à un type avec le composant <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à un type personnalisé à l'aide d'un composant <xref:System.Windows.Forms.BindingSource>. Lors de l'exécution de l'exemple, vous remarquerez que le <xref:System.Windows.Forms.DataGridView> a étiqueté les colonnes qui reflètent les propriétés d'un objet `Customer`, avant que le contrôle soit rempli avec des données. L'exemple comporte un bouton Add Customer pour ajouter des données au contrôle <xref:System.Windows.Forms.DataGridView>. Quand vous cliquez sur le bouton, un nouvel objet `Customer` est ajouté à <xref:System.Windows.Forms.BindingSource>. Dans un scénario réel, les données peuvent être obtenues par un appel à un service web ou autre source de données.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, composant](bindingsource-component.md)
