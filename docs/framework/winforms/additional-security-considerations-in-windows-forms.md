---
title: Considérations supplémentaires sur la sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739807"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Considérations supplémentaires sur la sécurité des Windows Forms
.NET Framework paramètres de sécurité peuvent entraîner une exécution différente de votre application dans un environnement de confiance partielle que sur votre ordinateur local. Le .NET Framework restreint l’accès à ces ressources locales critiques comme le système de fichiers, le réseau et les API non managées, entre autres choses. Les paramètres de sécurité affectent la possibilité d’appeler l’API Microsoft Windows ou d’autres API qui ne peuvent pas être vérifiées par le système de sécurité. La sécurité affecte également les autres aspects de votre application, y compris l’accès aux fichiers et aux données, ainsi que l’impression. Pour plus d’informations sur l’accès aux fichiers et aux données dans un environnement à confiance partielle, consultez [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Pour plus d’informations sur l’impression dans un environnement à confiance partielle, consultez [Impression plus sécurisée dans les Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 Les sections suivantes expliquent comment utiliser le presse-papiers, effectuer une manipulation de fenêtre et appeler l’API Windows à partir d’applications qui s’exécutent dans un environnement de confiance partielle.  
  
## <a name="clipboard-access"></a>Accès au presse-papiers  
 La classe <xref:System.Security.Permissions.UIPermission> contrôle l’accès au Presse-papiers, et la valeur d’énumération <xref:System.Security.Permissions.UIPermissionClipboard> associée indique le niveau d’accès. Le tableau suivant présente les différents niveaux d’autorisation.  
  
|Valeur UIPermissionClipboard|Description|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Le Presse-papiers peut être utilisé sans aucune restriction.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Le Presse-papiers peut être utilisé avec certaines restrictions. La possibilité de placer des données dans le Presse-papiers (opérations de commande copier ou couper) n’est pas restreinte. Les contrôles intrinsèques qui acceptent le collage, comme les zones de texte, peuvent accepter les données du Presse-papiers, mais les contrôles utilisateur ne peuvent pas lire le contenu du Presse-papiers par programme.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Impossible d’utiliser le Presse-papiers.|  
  
 Par défaut, la zone Intranet local reçoit <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> accès et la zone Internet reçoit <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> accès. Cela signifie que l’application peut copier des données dans le Presse-papiers, mais pas les coller par programme vers ou lire à partir du Presse-papiers. Ces restrictions empêchent les programmes sans confiance totale de lire les données copiées dans le Presse-papiers par une autre application. Si votre application nécessite l’accès total au Presse-papiers mais que vous n’avez pas les autorisations, vous devez élever les autorisations pour votre application. Pour plus d’informations sur l’élévation d’autorisations, consultez [Administration de la stratégie de sécurité générale](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulation de fenêtres  
 La classe <xref:System.Security.Permissions.UIPermission> contrôle également l’autorisation d’effectuer une manipulation de fenêtre et d’autres actions liées à l’interface utilisateur, et la valeur d’énumération <xref:System.Security.Permissions.UIPermissionWindow> associée indique le niveau d’accès. Le tableau suivant présente les différents niveaux d’autorisation.  
  
 Par défaut, la zone Intranet local reçoit <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> accès et la zone Internet reçoit <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> accès. Cela signifie que dans la zone Internet, l’application peut effectuer la plupart des actions d’interface utilisateur et liées aux fenêtres, mais l’aspect de la fenêtre sera modifié. La fenêtre modifiée affiche une bulle de notification lors du démarrage de l’exécution, contient le texte de barre de titre modifié et requiert un bouton Fermer dans la barre de titre. La bulle de notification et la barre de titre indiquent à l’utilisateur de l’application que l’application s’exécute en confiance partielle.  
  
|Valeur UIPermissionWindow|Description|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Les utilisateurs peuvent utiliser toutes les fenêtres et tous les événements d'entrée d'utilisateur sans restriction.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Les utilisateurs peuvent utiliser uniquement des fenêtres de niveau supérieur sûres et des sous-fenêtres sûres pour le dessin, et peuvent utiliser uniquement les événements d’entrée d’utilisateur pour l’interface utilisateur dans ces fenêtres de niveau supérieur et ces sous-fenêtres. Ces fenêtres sûres sont clairement indiquées et ont des restrictions de taille minimale et maximale. Les restrictions empêchent les attaques d’usurpation d’identité potentiellement dangereuses, telles que l’imitation des écrans d’ouverture de session système ou le Bureau du système, et limitent l’accès par programme aux fenêtres parentes, les API liées au focus et l’utilisation du contrôle <xref:System.Windows.Forms.ToolTip>,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Les utilisateurs peuvent utiliser uniquement des sous-fenêtres sûres pour le dessin, et peuvent utiliser uniquement les événements d’entrée d’utilisateur pour l’interface utilisateur dans ces sous-fenêtres. Un contrôle affiché dans un navigateur est un exemple de sous-fenêtre sûre.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Les utilisateurs ne peuvent pas utiliser d’événements d’interface utilisateur ou Windows. Aucune interface utilisateur ne peut être utilisée.|  
  
 Chaque niveau d’autorisation identifié par l’énumération <xref:System.Security.Permissions.UIPermissionWindow> autorise moins d’actions que le niveau supérieur. Les tableaux suivants indiquent les actions qui sont limitées par les valeurs <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> et <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>. Pour plus d'informations sur les autorisations nécessaires pour chaque membre, consultez la rubrique de référence correspondant à ce membre dans la documentation de la bibliothèque de classes .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> autorisation restreint les actions énumérées dans le tableau suivant.  
  
|Composant|Actions restreintes|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-   Définition de la propriété <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|-Obtention de la propriété <xref:System.Windows.Forms.Control.Parent%2A>.<br />-   Définition de la propriété `Region`.<br />-Appel de la méthode <xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> et <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>ou <xref:System.Windows.Forms.Control.SetTopLevel%2A>.<br />-Appel de la méthode <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> si le contrôle retourné n’est pas un enfant du contrôle appelant.<br />-   Modifier le focus du contrôle à l’intérieur d’un contrôle conteneur.|  
|<xref:System.Windows.Forms.Cursor>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />-Appel de la méthode <xref:System.Windows.Forms.Control.Hide%2A>.|  
|<xref:System.Windows.Forms.DataGrid>|-Appel de la méthode <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>.|  
|<xref:System.Windows.Forms.Form>|-Obtention de la propriété <xref:System.Windows.Forms.Form.ActiveForm%2A> ou <xref:System.Windows.Forms.Form.MdiParent%2A>.<br />-Définition de la propriété <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>ou <xref:System.Windows.Forms.Form.TopMost%2A>.<br />-Définition de la propriété <xref:System.Windows.Forms.Form.Opacity%2A> inférieure à 50%.<br />-Définition de la propriété <xref:System.Windows.Forms.Form.WindowState%2A> sur <xref:System.Windows.Forms.FormWindowState.Minimized> par programmation.<br />-Appel de la méthode <xref:System.Windows.Forms.Form.Activate%2A>.<br />-À l’aide des valeurs d’énumération <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>et <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle>.|  
|<xref:System.Windows.Forms.NotifyIcon>|-L’utilisation du composant <xref:System.Windows.Forms.NotifyIcon> est complètement restreinte.|  
  
 La valeur <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> restreint les actions énumérées dans le tableau suivant, en plus des restrictions placées par la valeur <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>.  
  
|Composant|Actions restreintes|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Avec une boîte de dialogue dérivée de la classe <xref:System.Windows.Forms.CommonDialog>.|  
|<xref:System.Windows.Forms.Control>|-Appel de la méthode <xref:System.Windows.Forms.Control.CreateGraphics%2A>.<br />-   Définition de la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|-Appel de la méthode <xref:System.Windows.Forms.Form.Show%2A>.|  
  
### <a name="hosting-third-party-controls"></a>Hébergement de contrôles tiers  
 Un autre type de manipulation de fenêtre peut se produire si vos formulaires hébergent des contrôles tiers. Un contrôle tiers est un <xref:System.Windows.Forms.UserControl> personnalisé que vous n’avez pas développé et compilé vous-même. Bien que le scénario d’hébergement soit difficile à exploiter, il est théoriquement possible pour un contrôle tiers de développer sa surface de rendu pour couvrir la zone entière de votre formulaire. Ce contrôle peut alors reproduire une boîte de dialogue critique et demander des informations telles que des combinaisons nom d’utilisateur/mot de passe ou des numéros de compte bancaire de vos utilisateurs.  
  
 Pour limiter ce risque, utilisez des contrôles tiers uniquement auprès de fournisseurs auxquels vous pouvez faire confiance. Si vous utilisez des contrôles tiers que vous avez téléchargés à partir d’une source non vérifiable, nous vous recommandons de vérifier le code source à la recherche d’attaques éventuelles. Après avoir vérifié que la source est non malveillante, vous devez compiler l’assembly vous-même pour garantir que la source correspond à l’assembly.  
  
## <a name="windows-api-calls"></a>Appels d’API Windows  
 Si la conception de votre application requiert l’appel d’une fonction à partir de l’API Windows, vous accédez au code non managé. Dans ce cas, les actions du code vers la fenêtre ou le système d’exploitation ne peuvent pas être déterminées lorsque vous utilisez des appels ou des valeurs de l’API Windows. La classe <xref:System.Security.Permissions.SecurityPermission> et la valeur <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> de l’énumération <xref:System.Security.Permissions.SecurityPermissionFlag> contrôlent l’accès au code non managé. Une application peut accéder à du code non managé uniquement quand l’autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> est accordée. Par défaut, seules les applications qui s'exécutent localement peuvent appeler du code non managé.  
  
 Certains membres de Windows Forms fournissent un accès non managé qui nécessite l’autorisation <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. Le tableau suivant répertorie les membres de l’espace de noms <xref:System.Windows.Forms> qui requièrent l’autorisation. Pour plus d’informations sur les autorisations requises pour un membre, consultez la documentation de la bibliothèque de classes .NET Framework.  
  
|Composant|Membre|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|Méthode -   <xref:System.Windows.Forms.Application.AddMessageFilter%2A><br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> propriété<br />Méthode -   `Exit`<br />Méthode -   <xref:System.Windows.Forms.Application.ExitThread%2A><br />événement -   <xref:System.Windows.Forms.Application.ThreadException>|  
|<xref:System.Windows.Forms.CommonDialog>|Méthode -   <xref:System.Windows.Forms.CommonDialog.HookProc%2A><br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\, méthode<br />Méthode -   <xref:System.Windows.Forms.CommonDialog.Reset%2A><br />Méthode -   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>|  
|<xref:System.Windows.Forms.Control>|Méthode -   <xref:System.Windows.Forms.Control.CreateParams%2A><br />Méthode -   <xref:System.Windows.Forms.Control.DefWndProc%2A><br />Méthode -   <xref:System.Windows.Forms.Control.DestroyHandle%2A><br />Méthode -   <xref:System.Windows.Forms.Control.WndProc%2A>|  
|<xref:System.Windows.Forms.Help>|méthodes de <xref:System.Windows.Forms.Help.ShowHelp%2A> -   <br />Méthode -   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>|  
|<xref:System.Windows.Forms.NativeWindow>|classe -   <xref:System.Windows.Forms.NativeWindow>|  
|<xref:System.Windows.Forms.Screen>|Méthode -   <xref:System.Windows.Forms.Screen.FromHandle%2A>|  
|<xref:System.Windows.Forms.SendKeys>|Méthode -   <xref:System.Windows.Forms.SendKeys.Send%2A><br />Méthode -   <xref:System.Windows.Forms.SendKeys.SendWait%2A>|  
  
 Si votre application n’a pas l’autorisation d’appeler du code non managé, votre application doit demander <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> autorisation, ou vous devez envisager d’autres méthodes d’implémentation des fonctionnalités. dans de nombreux cas, Windows Forms fournit une alternative managée aux fonctions de l’API Windows. En cas d’absence d’alternative et si l’application doit accéder à du code non managé, vous devez élever les autorisations pour l’application.  
  
 L’autorisation d’appeler du code non managé permet à une application d’exécuter pratiquement n’importe quoi. Par conséquent, l’autorisation d’appeler du code non managé doit uniquement être accordée pour les applications qui proviennent d’une source approuvée. Selon l’application, la fonctionnalité qui effectue l’appel au code non managé peut également être facultative ou activée uniquement dans l’environnement à confiance totale. Pour plus d’informations sur les autorisations, consultez [Autorisations dangereuses et administration de stratégie](../misc/dangerous-permissions-and-policy-administration.md). Pour plus d’informations sur l’élévation d’autorisations, consultez [Administration de la stratégie de sécurité générale](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Impression plus sécurisée dans les Windows Forms](more-secure-printing-in-windows-forms.md)
- [Vue d’ensemble de la sécurité dans les Windows Forms](security-in-windows-forms-overview.md)
- [Sécurité de Windows Forms](windows-forms-security.md)
- [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications)
