---
title: 'Procédure : ajouter des fonctionnalités de navigateur web à une application Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: c091d9473bb7c3540453cb5763052f45f61b61f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624002"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Procédure : ajouter des fonctionnalités de navigateur web à une application Windows Forms
Avec le contrôle <xref:System.Windows.Forms.WebBrowser>, vous pouvez ajouter des fonctionnalités de navigateur web à votre application. Le contrôle fonctionne comme un navigateur web par défaut. Après avoir chargé une URL initiale en définissant la propriété <xref:System.Windows.Forms.WebBrowser.Url%2A>, vous pouvez naviguer en cliquant sur des liens hypertexte ou en utilisant des raccourcis clavier pour parcourir l'historique de navigation. Par défaut, vous pouvez accéder à d'autres fonctionnalités de navigateur via le menu contextuel. Vous pouvez aussi ouvrir de nouveaux documents en les déposant sur le contrôle. Le contrôle <xref:System.Windows.Forms.WebBrowser> possède également plusieurs propriétés, méthodes et événements que vous pouvez utiliser pour implémenter des fonctionnalités d'interface utilisateur semblables à celles d'Internet Explorer.  
  
 L’exemple de code suivant implémente une barre d’adresses, des boutons de navigateur courants, un menu **Fichier**, une barre d’état et une barre de titre qui affiche le titre de la page actuelle.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys `System`, `System.Drawing` et `System.Windows.Forms`.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser, contrôle](webbrowser-control-windows-forms.md)
