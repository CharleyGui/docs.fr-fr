---
title: 'Procédure : Retourner un résultat de boîte de dialogue'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968229"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="70070-102">Procédure : Retourner un résultat de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="70070-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="70070-103">Cet exemple montre comment récupérer le résultat de la boîte de dialogue pour une fenêtre ouverte en <xref:System.Windows.Window.ShowDialog%2A>appelant.</span><span class="sxs-lookup"><span data-stu-id="70070-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70070-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="70070-104">Example</span></span>  
 <span data-ttu-id="70070-105">Avant la fermeture d’une boîte de <xref:System.Windows.Window.DialogResult%2A> dialogue, sa propriété doit être <xref:System.Nullable%601> définie avec une valeur qui indique la façon dont l’utilisateur a <xref:System.Boolean> fermé la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="70070-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="70070-106">Cette valeur est retournée <xref:System.Windows.Window.ShowDialog%2A> par pour permettre au code client de déterminer comment la boîte de dialogue a été fermée et, par conséquent, comment traiter le résultat.</span><span class="sxs-lookup"><span data-stu-id="70070-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70070-107"><xref:System.Windows.Window.DialogResult%2A>ne peut être défini que si une fenêtre a été ouverte <xref:System.Windows.Window.ShowDialog%2A>en appelant.</span><span class="sxs-lookup"><span data-stu-id="70070-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="70070-108">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="70070-108">.NET Framework Security</span></span>  
 <span data-ttu-id="70070-109">L' <xref:System.Windows.Window.ShowDialog%2A> appel de requiert l’autorisation d’utiliser tous les événements d’entrée de Windows et d’utilisateur sans restriction.</span><span class="sxs-lookup"><span data-stu-id="70070-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
