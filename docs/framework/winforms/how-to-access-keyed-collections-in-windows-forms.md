---
title: 'Procédure : accéder à des collections à clé dans Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 47bd0ff4eb649b4b32113a984f4aa99cd4afc0f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665275"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="6085d-102">Procédure : accéder à des collections à clé dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6085d-102">How to: Access Keyed Collections in Windows Forms</span></span>
- <span data-ttu-id="6085d-103">Vous pouvez accéder à des éléments de collection individuels par clé.</span><span class="sxs-lookup"><span data-stu-id="6085d-103">You can access individual collection items by key.</span></span> <span data-ttu-id="6085d-104">Cette fonctionnalité a été ajoutée à de nombreuses classes de collection sont généralement utilisées par les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6085d-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="6085d-105">La liste suivante présente certaines des classes de collection qui ont des collections à clé accessibles :</span><span class="sxs-lookup"><span data-stu-id="6085d-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="6085d-106">La clé associée à un élément dans une collection est généralement le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6085d-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="6085d-107">Les procédures suivantes vous montrent comment utiliser les classes de collection pour effectuer des tâches courantes.</span><span class="sxs-lookup"><span data-stu-id="6085d-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="6085d-108">Pour rechercher et de donner le focus à un contrôle imbriqué dans un regroupement de contrôle</span><span class="sxs-lookup"><span data-stu-id="6085d-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="6085d-109">Utilisez le <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> et <xref:System.Windows.Forms.Control.Focus%2A> méthodes pour spécifier le nom du contrôle à rechercher et de donner le focus à.</span><span class="sxs-lookup"><span data-stu-id="6085d-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="6085d-110">Pour accéder à une image dans une collection d’images</span><span class="sxs-lookup"><span data-stu-id="6085d-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="6085d-111">Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> propriété pour spécifier le nom de l’image que vous souhaitez accéder.</span><span class="sxs-lookup"><span data-stu-id="6085d-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="6085d-112">Pour définir une page d’onglets en tant que l’onglet sélectionné</span><span class="sxs-lookup"><span data-stu-id="6085d-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="6085d-113">Utilisez le <xref:System.Windows.Forms.TabControl.SelectedTab%2A> propriété avec le <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> propriété pour spécifier le nom de la page d’onglets à définir comme onglet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6085d-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6085d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6085d-114">See also</span></span>

- [<span data-ttu-id="6085d-115">Bien démarrer avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6085d-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="6085d-116">Guide pratique pour Ajouter ou supprimer des Images avec le composant ImageList Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6085d-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
