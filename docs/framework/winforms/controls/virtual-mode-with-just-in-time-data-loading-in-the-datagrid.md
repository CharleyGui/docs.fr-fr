---
title: 'Procédure : implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: 82a6e7bd1bb112c3341e7aefb4a3722d3c2be056
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592910"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="23a54-102">Procédure : implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23a54-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="23a54-103">L'exemple de code suivant montre comment utiliser le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> avec un cache de données qui charge des données à partir d'un serveur uniquement en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="23a54-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="23a54-104">Cet exemple est décrit en détail dans [implémentation du Mode virtuel avec le chargement de données juste à temps dans le contrôle de DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="23a54-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a54-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="23a54-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23a54-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="23a54-106">Compiling the Code</span></span>  
 <span data-ttu-id="23a54-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="23a54-107">This example requires:</span></span>  
  
- <span data-ttu-id="23a54-108">des références aux assemblys System.Data, System.Xml et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="23a54-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="23a54-109">l'accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.</span><span class="sxs-lookup"><span data-stu-id="23a54-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="23a54-110">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="23a54-110">.NET Framework Security</span></span>  
 <span data-ttu-id="23a54-111">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="23a54-111">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="23a54-112">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="23a54-112">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="23a54-113">Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="23a54-113">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a54-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23a54-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="23a54-115">Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23a54-115">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="23a54-116">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23a54-116">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="23a54-117">Mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23a54-117">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
