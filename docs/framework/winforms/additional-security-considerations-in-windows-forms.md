---
title: Considérations supplémentaires sur la sécurité des Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: 3049b56589b2cd7f5e6cab462955a67289315b35
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588777"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Considérations supplémentaires sur la sécurité des Windows Forms
Paramètres de sécurité de .NET framework peuvent conduire votre application à s’exécuter différemment dans un environnement de confiance partielle sur votre ordinateur local. Le .NET Framework limite l’accès aux ressources locales critiques, comme le système de fichiers, réseau et les API non managées, entre autres choses. Les paramètres de sécurité affectent la possibilité d’appeler l’API Windows de Microsoft ou d’autres API qui ne peut pas être vérifié par le système de sécurité. La sécurité affecte également les autres aspects de votre application, y compris l’accès aux fichiers et aux données, ainsi que l’impression. Pour plus d’informations sur l’accès aux fichiers et aux données dans un environnement à confiance partielle, consultez [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Pour plus d’informations sur l’impression dans un environnement à confiance partielle, consultez [Impression plus sécurisée dans les Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 Les sections suivantes expliquent comment utiliser le Presse-papiers, effectuer une manipulation de fenêtre et appeler l’API de Windows à partir d’applications qui sont exécutent dans un environnement de confiance partielle.  
  
## <a name="clipboard-access"></a>Accès au presse-papiers  
 Le <xref:System.Security.Permissions.UIPermission> classe contrôle l’accès vers le Presse-papiers et associé <xref:System.Security.Permissions.UIPermissionClipboard> valeur d’énumération indique le niveau d’accès. Le tableau suivant présente les différents niveaux d’autorisation.  
  
|Valeur UIPermissionClipboard|Description|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Le Presse-papiers peut être utilisé sans aucune restriction.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Le Presse-papiers peut être utilisé avec certaines restrictions. La possibilité de placer des données dans le Presse-papiers (opérations de commande copier ou couper) n’est pas restreinte. Les contrôles intrinsèques qui acceptent le collage, comme les zones de texte, peuvent accepter les données du Presse-papiers, mais les contrôles utilisateur ne peuvent pas lire le contenu du Presse-papiers par programme.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Impossible d’utiliser le Presse-papiers.|  
  
 Par défaut, la zone Intranet locale reçoit <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> accès et la zone Internet reçoit <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> accès. Cela signifie que l’application peut copier des données dans le Presse-papiers, mais pas les coller par programme vers ou lire à partir du Presse-papiers. Ces restrictions empêchent les programmes sans confiance totale de lire les données copiées dans le Presse-papiers par une autre application. Si votre application nécessite l’accès total au Presse-papiers mais que vous n’avez pas les autorisations, vous devez élever les autorisations pour votre application. Pour plus d’informations sur l’élévation d’autorisations, consultez [Administration de la stratégie de sécurité générale](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulation de fenêtres  
 Le <xref:System.Security.Permissions.UIPermission> classe contrôle également l’autorisation d’effectuer des manipulations de fenêtres et autres actions liées à l’interface utilisateur, ainsi que le <xref:System.Security.Permissions.UIPermissionWindow> valeur d’énumération indique le niveau d’accès. Le tableau suivant présente les différents niveaux d’autorisation.  
  
 Par défaut, la zone Intranet locale reçoit <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> accès et la zone Internet reçoit <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> accès. Cela signifie que dans la zone Internet, l’application peut effectuer la plupart des actions d’interface utilisateur et liées aux fenêtres, mais l’aspect de la fenêtre sera modifié. La fenêtre modifiée affiche une bulle de notification lors du démarrage de l’exécution, contient le texte de barre de titre modifié et requiert un bouton Fermer dans la barre de titre. La bulle de notification et la barre de titre indiquent à l’utilisateur de l’application que l’application s’exécute en confiance partielle.  
  
|Valeur UIPermissionWindow|Description|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Les utilisateurs peuvent utiliser toutes les fenêtres et tous les événements d'entrée d'utilisateur sans restriction.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Les utilisateurs peuvent utiliser uniquement des fenêtres de niveau supérieur sûres et des sous-fenêtres sûres pour le dessin, et peuvent utiliser uniquement les événements d’entrée d’utilisateur pour l’interface utilisateur dans ces fenêtres de niveau supérieur et ces sous-fenêtres. Ces fenêtres sûres sont clairement indiquées et ont des restrictions de taille minimale et maximale. Les restrictions empêchent les attaques d’usurpation d’identité potentiellement dangereux, comme l’imitation des écrans d’ouverture de session système ou le bureau du système et limite l’accès par programme aux fenêtres parentes, API liées au focus et l’utilisation de la <xref:System.Windows.Forms.ToolTip> contrôle,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Les utilisateurs peuvent utiliser uniquement des sous-fenêtres sûres pour le dessin, et peuvent utiliser uniquement les événements d’entrée d’utilisateur pour l’interface utilisateur dans ces sous-fenêtres. Un contrôle affiché dans un navigateur est un exemple de sous-fenêtre sûre.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Les utilisateurs ne peuvent pas utiliser d’événements d’interface utilisateur ou Windows. Aucune interface utilisateur ne peut être utilisée.|  
  
 Chaque niveau d’autorisation identifié par le <xref:System.Security.Permissions.UIPermissionWindow> énumération permet de moins d’actions que le niveau immédiatement supérieur. Les tableaux suivants indiquent les actions qui sont limitées par le <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> et <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> valeurs. Pour plus d'informations sur les autorisations nécessaires pour chaque membre, consultez la rubrique de référence correspondant à ce membre dans la documentation de la bibliothèque de classes .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> autorisation restreint les actions répertoriées dans le tableau suivant.  
  
|Composant|Actions restreintes|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-   Définition de la propriété <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|-Obtention de la <xref:System.Windows.Forms.Control.Parent%2A> propriété.<br />-   Définition de la propriété `Region`.<br />-Appel de la <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> et <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, ou <xref:System.Windows.Forms.Control.SetTopLevel%2A> (méthode).<br />-Appel de la <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> méthode si le contrôle retourné n’est pas un enfant du contrôle appelant.<br />-   Modifier le focus du contrôle à l’intérieur d’un contrôle conteneur.|  
|<xref:System.Windows.Forms.Cursor>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />-Appel de la <xref:System.Windows.Forms.Control.Hide%2A> (méthode).|  
|<xref:System.Windows.Forms.DataGrid>|-Appel de la <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> (méthode).|  
|<xref:System.Windows.Forms.Form>|-Obtention de la <xref:System.Windows.Forms.Form.ActiveForm%2A> ou <xref:System.Windows.Forms.Form.MdiParent%2A> propriété.<br />-Définition de la <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, ou <xref:System.Windows.Forms.Form.TopMost%2A> propriété.<br />-Définition de la <xref:System.Windows.Forms.Form.Opacity%2A> propriété inférieure à 50 %.<br />-Définition de la <xref:System.Windows.Forms.Form.WindowState%2A> propriété <xref:System.Windows.Forms.FormWindowState.Minimized> par programmation.<br />-Appel de la <xref:System.Windows.Forms.Form.Activate%2A> (méthode).<br />-À l’aide de la <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, et <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> valeurs d’énumération.|  
|<xref:System.Windows.Forms.NotifyIcon>|-À l’aide de la <xref:System.Windows.Forms.NotifyIcon> composant est complètement restreint.|  
  
 Le <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> valeur restreint les actions répertoriées dans le tableau suivant, en outre à des restrictions imposées par le <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> valeur.  
  
|Composant|Actions restreintes|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Affiche une boîte de dialogue dérivée de la <xref:System.Windows.Forms.CommonDialog> classe.|  
|<xref:System.Windows.Forms.Control>|-Appel de la <xref:System.Windows.Forms.Control.CreateGraphics%2A> (méthode).<br />-   Définition de la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|-Appel de la <xref:System.Windows.Forms.Form.Show%2A> (méthode).|  
  
### <a name="hosting-third-party-controls"></a>Hébergement de contrôles tiers  
 Un autre type de manipulation de fenêtre peut se produire si vos formulaires hébergent des contrôles tiers. Un contrôle tiers est n’importe quel custom <xref:System.Windows.Forms.UserControl> que vous n’avez pas développé et compilé vous-même. Bien que le scénario d’hébergement soit difficile à exploiter, il est théoriquement possible pour un contrôle tiers de développer sa surface de rendu pour couvrir la zone entière de votre formulaire. Ce contrôle peut alors reproduire une boîte de dialogue critique et demander des informations telles que des combinaisons nom d’utilisateur/mot de passe ou des numéros de compte bancaire de vos utilisateurs.  
  
 Pour limiter ce risque, utilisez des contrôles tiers uniquement auprès de fournisseurs auxquels vous pouvez faire confiance. Si vous utilisez des contrôles tiers que vous avez téléchargés à partir d’une source non vérifiable, nous vous recommandons de vérifier le code source à la recherche d’attaques éventuelles. Après avoir vérifié que la source est non malveillante, vous devez compiler l’assembly vous-même pour garantir que la source correspond à l’assembly.  
  
## <a name="windows-api-calls"></a>Appels d’API Windows  
 Si la conception de votre application, vous devez appeler une fonction à partir de l’API Windows, vous accédez au code non managé. Dans ce cas, les actions du code dans la fenêtre ou le système d’exploitation ne peut pas être déterminées lorsque vous travaillez avec les valeurs ou les appels d’API de Windows. Le <xref:System.Security.Permissions.SecurityPermission> classe et le <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> valeur de la <xref:System.Security.Permissions.SecurityPermissionFlag> contrôlent l’accès au code non managé. Une application peut accéder de code non managé uniquement lorsqu’elle est accordée le <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> autorisation. Par défaut, seules les applications qui s'exécutent localement peuvent appeler du code non managé.  
  
 Certains membres Windows Forms fournissent un accès non managé nécessitant le <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> autorisation. Le tableau suivant répertorie les membres dans le <xref:System.Windows.Forms> espace de noms qui nécessitent l’autorisation. Pour plus d’informations sur les autorisations requises pour un membre, consultez la documentation de la bibliothèque de classes .NET Framework.  
  
|Composant|Membre|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|Méthode -   <xref:System.Windows.Forms.Application.AddMessageFilter%2A><br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Propriété<br />Méthode -   `Exit`<br />Méthode -   <xref:System.Windows.Forms.Application.ExitThread%2A><br />-   <xref:System.Windows.Forms.Application.ThreadException> Événement|  
|<xref:System.Windows.Forms.CommonDialog>|Méthode -   <xref:System.Windows.Forms.CommonDialog.HookProc%2A><br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ (méthode)<br />Méthode -   <xref:System.Windows.Forms.CommonDialog.Reset%2A><br />Méthode -   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>|  
|<xref:System.Windows.Forms.Control>|Méthode -   <xref:System.Windows.Forms.Control.CreateParams%2A><br />Méthode -   <xref:System.Windows.Forms.Control.DefWndProc%2A><br />Méthode -   <xref:System.Windows.Forms.Control.DestroyHandle%2A><br />Méthode -   <xref:System.Windows.Forms.Control.WndProc%2A>|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Méthodes<br />Méthode -   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> Classe|  
|<xref:System.Windows.Forms.Screen>|Méthode -   <xref:System.Windows.Forms.Screen.FromHandle%2A>|  
|<xref:System.Windows.Forms.SendKeys>|Méthode -   <xref:System.Windows.Forms.SendKeys.Send%2A><br />Méthode -   <xref:System.Windows.Forms.SendKeys.SendWait%2A>|  
  
 Si votre application n’a pas d’autorisation d’appeler du code non managé, votre application doit demander <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> autorisation, ou vous devez envisager d’autres moyens d’implémenter des fonctionnalités ; dans de nombreux cas, Windows Forms offrent une alternative managée pour Windows Fonctions d’API. En cas d’absence d’alternative et si l’application doit accéder à du code non managé, vous devez élever les autorisations pour l’application.  
  
 L’autorisation d’appeler du code non managé permet à une application d’exécuter pratiquement n’importe quoi. Par conséquent, l’autorisation d’appeler du code non managé doit uniquement être accordée pour les applications qui proviennent d’une source approuvée. Selon l’application, la fonctionnalité qui effectue l’appel au code non managé peut également être facultative ou activée uniquement dans l’environnement à confiance totale. Pour plus d’informations sur les autorisations, consultez [Autorisations dangereuses et administration de stratégie](../misc/dangerous-permissions-and-policy-administration.md). Pour plus d’informations sur l’élévation d’autorisations, consultez [Administration de la stratégie de sécurité générale](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Impression plus sécurisée dans les Windows Forms](more-secure-printing-in-windows-forms.md)
- [Vue d’ensemble de la sécurité dans les Windows Forms](security-in-windows-forms-overview.md)
- [Sécurité de Windows Forms](windows-forms-security.md)
- [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
