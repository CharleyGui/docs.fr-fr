---
title: 'Procédure : parcourir un jeu de données avec le contrôle BindingNavigator de Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952696"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="bcecd-102">Procédure : parcourir un jeu de données avec le contrôle BindingNavigator de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bcecd-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="bcecd-103">Quand vous générez des applications pilotées par les données, vous devez souvent présenter des collections de données aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bcecd-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="bcecd-104">Le contrôle <xref:System.Windows.Forms.BindingNavigator>, associé au composant <xref:System.Windows.Forms.BindingSource>, fournit une solution pratique et extensible pour parcourir une collection et afficher des éléments de façon séquentielle.</span><span class="sxs-lookup"><span data-stu-id="bcecd-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcecd-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcecd-105">Example</span></span>  
 <span data-ttu-id="bcecd-106">L'exemple de code suivant montre comment utiliser un contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir des données.</span><span class="sxs-lookup"><span data-stu-id="bcecd-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="bcecd-107">Le jeu est contenu dans un <xref:System.Data.DataView>, qui est lié à un contrôle <xref:System.Windows.Forms.TextBox> avec un composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="bcecd-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcecd-108">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="bcecd-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="bcecd-109">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="bcecd-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="bcecd-110">Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="bcecd-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bcecd-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bcecd-111">Compiling the Code</span></span>  
 <span data-ttu-id="bcecd-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="bcecd-112">This example requires:</span></span>  
  
- <span data-ttu-id="bcecd-113">Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="bcecd-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcecd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcecd-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="bcecd-115">BindingNavigator, contrôle</span><span class="sxs-lookup"><span data-stu-id="bcecd-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="bcecd-116">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="bcecd-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="bcecd-117">Guide pratique pour Lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="bcecd-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
