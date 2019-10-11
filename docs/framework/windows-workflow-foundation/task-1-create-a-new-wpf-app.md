---
title: 'Tâche 1 : créer une application Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031899"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Tâche 1 : créer une application Windows Presentation Foundation

Dans cette tâche, vous allez créer une application Windows Presentation Foundatione (WPF) vide à l’aide du modèle Visual Studio d’application WPF et ajouter des références aux assemblys de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] appropriés.  
  
## <a name="to-create-the-wpf-application-project"></a>Pour créer le projet d'application WPF

1. Ouvrez Visual Studio et, dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **projet**.

2. Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#**  ou **Visual Basic** dans le volet **modèles installés** sur le côté gauche de la zone. Si la langue de votre choix n’apparaît pas, recherchez dans **autres langues**.

3. Sélectionnez **Windows** dans le volet **modèles installés** .

4. Dans le volet supérieur, vérifiez que (la valeur par défaut) **.NET Framework 4** a été sélectionné dans la zone de liste déroulante, puis sélectionnez **application WPF**.

5. Définissez le nom du projet sur **HostingApplication** en bas de la fenêtre.

6. Définissez le nom de la solution sur **RehostingTheDesigner**.

7. Cliquez sur **OK** pour créer le projet d’application. Visual Studio crée une interface utilisateur WPF de base pour votre application et comprend les fichiers XAML et code-behind appropriés.

8. Ajoutez des références aux assemblys **WorkflowModel** . Pour ce faire, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **HostingApplication** , puis sélectionnez **Ajouter une référence**.

9. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **.net** , maintenez la touche CTRL enfoncée, sélectionnez les assemblys suivants, puis cliquez sur **OK**:

    - System.Activities
    - System.Activities.Presentation
    - System.Activities.Core.Presentation

10. Voir [Task 2 : Hébergez le Concepteur de flux de travail @ no__t-0 pour apprendre à héberger la zone de conception du concepteur de Workflow.

## <a name="see-also"></a>Voir aussi

- [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)
- @no__t 0Task 2 : Héberger le Concepteur de flux de travail @ no__t-0
