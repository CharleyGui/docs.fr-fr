---
title: Valider les données dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728307"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="51e76-102">Comment : valider des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51e76-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="51e76-103">L'exemple de code suivant montre comment valider les données entrées par un utilisateur dans un contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="51e76-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="51e76-104">Dans cet exemple, le <xref:System.Windows.Forms.DataGridView> est rempli avec des lignes de la table `Customers` de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="51e76-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="51e76-105">Quand l'utilisateur modifie une cellule dans la colonne `CompanyName`, la validité de sa valeur est testée en vérifiant qu'elle n'est pas vide.</span><span class="sxs-lookup"><span data-stu-id="51e76-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="51e76-106">Si le gestionnaire d'événements de l'événement <xref:System.Windows.Forms.DataGridView.CellValidating> détecte que la valeur est une chaîne vide, le <xref:System.Windows.Forms.DataGridView> empêche l'utilisateur de quitter la cellule tant qu'il n'a pas entré une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="51e76-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="51e76-107">Pour obtenir une explication complète de cet exemple de code, consultez [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="51e76-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51e76-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="51e76-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51e76-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="51e76-109">Compiling the Code</span></span>  
 <span data-ttu-id="51e76-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="51e76-110">This example requires:</span></span>  
  
- <span data-ttu-id="51e76-111">Références aux assemblys System, System.Data, System.Windows.Forms et System.XML.</span><span class="sxs-lookup"><span data-stu-id="51e76-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="51e76-112">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="51e76-112">.NET Framework Security</span></span>  
 <span data-ttu-id="51e76-113">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="51e76-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="51e76-114">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="51e76-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="51e76-115">Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="51e76-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e76-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51e76-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="51e76-117">Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51e76-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="51e76-118">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51e76-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="51e76-119">Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51e76-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="51e76-120">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="51e76-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
