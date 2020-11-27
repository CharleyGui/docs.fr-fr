---
title: 'Procédure : créer un modèle d’activité personnalisé'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 90a54806833ff66797fb7beaa6ac8a912665bddc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280115"
---
# <a name="how-to-create-a-custom-activity-template"></a>Procédure : créer un modèle d’activité personnalisé

Les modèles d'activité personnalisés sont utilisés pour personnaliser la configuration des activités, parmi lesquelles les activités composites personnalisées, afin que les utilisateurs n'aient pas besoin de créer individuellement chaque activité et de configurer manuellement leurs propriétés et les autres paramètres. Ces modèles personnalisés peuvent être rendus disponibles dans la **boîte à outils** de Windows concepteur de flux de travail ou d’un concepteur réhébergé, à partir duquel les utilisateurs peuvent les faire glisser sur l’aire de conception préconfigurée. Concepteur de flux de travail est fourni avec de bons exemples de ces modèles : le concepteur de modèles [SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) et le [Concepteur de modèles ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) dans la catégorie des [concepteurs d’activités de messagerie](/visualstudio/workflow-designer/messaging-activity-designers) .

 La première procédure de cette rubrique décrit comment créer un modèle d’activité personnalisé pour une activité **delay** et la deuxième procédure décrit brièvement comment le rendre disponible dans une concepteur de flux de travail pour vérifier que le modèle personnalisé fonctionne.

 Les modèles d'activité personnalisés doivent implémenter l'<xref:System.Activities.Presentation.IActivityTemplateFactory>. L'interface dispose d'une seule méthode <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> avec laquelle vous pouvez créer et configurer les instances d'activité utilisées dans le modèle.

## <a name="to-create-a-template-for-the-delay-activity"></a>Pour créer un modèle pour l'activité Delay

1. Démarrez Visual Studio 2010.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **types de projets** , sélectionnez flux de **travail** à partir des projets **Visual C#** ou **Visual Basic** regroupements en fonction de vos préférences linguistiques.

4. Dans le volet **modèles** , sélectionnez **bibliothèque d’activités**.

5. Dans la zone **Nom**, entrez `DelayActivityTemplate`.

6. Acceptez les valeurs par défaut dans les zones de texte **emplacement** et nom de la **solution** , puis cliquez sur **OK**.

7. Cliquez avec le bouton droit sur le répertoire References du projet DelayActivityTemplate dans **Explorateur de solutions** , puis choisissez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence** .

8. Accédez à l’onglet **.net** et sélectionnez **PresentationFramework** dans la colonne **nom du composant** sur la gauche, puis cliquez sur **OK** pour ajouter une référence au fichier PresentationFramework.dll.

9. Répétez cette procédure pour ajouter des références aux fichiers System.Activities.Presentation.dll et WindowsBase.dll.

10. Cliquez avec le bouton droit sur le projet DelayActivityTemplate dans **Explorateur de solutions** , puis choisissez **Ajouter** , puis **nouvel élément** pour ouvrir la boîte de dialogue **Ajouter un nouvel élément** .

11. Sélectionnez le modèle de **classe** , nommez-le MyDelayTemplate, puis cliquez sur **OK**.

12. Ouvrez le fichier MyDelayTemplate.cs et ajoutez les instructions suivantes.

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implémentez <xref:System.Activities.Presentation.IActivityTemplateFactory> avec la classe `MyDelayActivity` dans le code suivant. Cela configure une durée de 10 secondes comme délai.

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. Sélectionnez **générer la solution** dans le menu **générer** pour générer le fichier DelayActivityTemplate.dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Pour rendre le modèle disponible dans un concepteur de workflow

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur la solution DelayActivityTemplate et choisissez **Ajouter** , puis **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

2. Sélectionnez le modèle **application console de workflow** , nommez-le `CustomActivityTemplateApp` , puis cliquez sur **OK**.

3. Cliquez avec le bouton droit sur le répertoire References du projet CustomActivityTemplateApp dans **Explorateur de solutions** , puis choisissez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence** .

4. Accédez à l’onglet **projets** et sélectionnez **DelayActivityTemplate** dans la colonne **nom du projet** à gauche, puis cliquez sur **OK** pour ajouter une référence au fichier DelayActivityTemplate.dll que vous avez créé dans la première procédure.

5. Cliquez avec le bouton droit sur le projet CustomActivityTemplateApp dans **Explorateur de solutions** , puis choisissez **générer** pour compiler l’application.

6. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet CustomActivityTemplateApp, puis choisissez **définir comme projet de démarrage**.

7. Sélectionnez **exécuter sans débogage** dans le menu **Déboguer** et appuyez sur n’importe quelle touche pour continuer quand vous y êtes invité dans la fenêtre de cmd.exe.

8. Ouvrez le fichier Workflow1. xaml et ouvrez la **boîte à outils**.

9. Recherchez le modèle **MyDelayActivity** dans la catégorie **DelayActivityTemplate** . Faites-le glisser vers l'aire de conception. Dans la fenêtre **Propriétés** , vérifiez que la `Duration` propriété a été définie sur 10 secondes.

## <a name="example"></a> Exemple

 Le fichier MyDelayActivity.cs doit contenir le code suivant.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [Personnalisation de l'expérience de conception de workflow](customizing-the-workflow-design-experience.md)
