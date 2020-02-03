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
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="fc9a5-102">Comment : lier un contrôle Windows Forms à un objet Factory</span><span class="sxs-lookup"><span data-stu-id="fc9a5-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="fc9a5-103">Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un objet ou à une méthode qui génère d'autres objets.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="fc9a5-104">Un tel objet ou une telle méthode porte le nom de fabrique.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="fc9a5-105">Votre source de données peut par exemple être la valeur de retour d'un appel de méthode, plutôt qu'un objet en mémoire ou un type.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="fc9a5-106">Vous pouvez lier un contrôle à ce genre de source de données tant que la source retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="fc9a5-107">Vous pouvez facilement lier un contrôle à un objet de fabrique à l'aide du contrôle <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc9a5-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="fc9a5-108">Example</span></span>  
 <span data-ttu-id="fc9a5-109">L'exemple suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à une méthode de fabrique à l'aide d'un contrôle <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="fc9a5-110">La méthode de fabrique se nomme `GetOrdersByCustomerId` et retourne toutes les commandes pour un client donné dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc9a5-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fc9a5-111">Compiling the Code</span></span>  
 <span data-ttu-id="fc9a5-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="fc9a5-112">This example requires:</span></span>  
  
- <span data-ttu-id="fc9a5-113">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fc9a5-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9a5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc9a5-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="fc9a5-115">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="fc9a5-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="fc9a5-116">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="fc9a5-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
