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
# <a name="how-to-return-a-dialog-box-result"></a>Procédure : Retourner un résultat de boîte de dialogue
Cet exemple montre comment récupérer le résultat de la boîte de dialogue pour une fenêtre ouverte en <xref:System.Windows.Window.ShowDialog%2A>appelant.  
  
## <a name="example"></a>Exemple  
 Avant la fermeture d’une boîte de <xref:System.Windows.Window.DialogResult%2A> dialogue, sa propriété doit être <xref:System.Nullable%601> définie avec une valeur qui indique la façon dont l’utilisateur a <xref:System.Boolean> fermé la boîte de dialogue. Cette valeur est retournée <xref:System.Windows.Window.ShowDialog%2A> par pour permettre au code client de déterminer comment la boîte de dialogue a été fermée et, par conséquent, comment traiter le résultat.  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>ne peut être défini que si une fenêtre a été ouverte <xref:System.Windows.Window.ShowDialog%2A>en appelant.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 L' <xref:System.Windows.Window.ShowDialog%2A> appel de requiert l’autorisation d’utiliser tous les événements d’entrée de Windows et d’utilisateur sans restriction.
