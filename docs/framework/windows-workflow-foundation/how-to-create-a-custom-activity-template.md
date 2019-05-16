---
title: 'Procédure : créer un modèle d’activité personnalisé'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f54a625fbe5497406645ea29f824d361c0392eb3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637724"
---
# <a name="how-to-create-a-custom-activity-template"></a>Procédure : créer un modèle d’activité personnalisé

Les modèles d'activité personnalisés sont utilisés pour personnaliser la configuration des activités, parmi lesquelles les activités composites personnalisées, afin que les utilisateurs n'aient pas besoin de créer individuellement chaque activité et de configurer manuellement leurs propriétés et les autres paramètres. Ces modèles personnalisés peuvent être rendus disponibles dans le **boîte à outils** sur la [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou à partir d’un concepteur réhébergé, à partir de laquelle les utilisateurs peuvent les faire glisser sur l’aire de conception préconfigurée. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] est fourni avec de bons exemples de ces modèles : le [Concepteur de modèles SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) et [Concepteur de modèles ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) dans le [concepteurs d’activités de messagerie](/visualstudio/workflow-designer/messaging-activity-designers) catégorie.

 La première procédure de cette rubrique décrit comment créer un modèle d’activité personnalisée pour un **délai** activité et la seconde procédure explique brièvement comment rendre disponible dans un [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] pour vérifier que le modèle personnalisé fonctionne.

 Les modèles d'activité personnalisés doivent implémenter l'<xref:System.Activities.Presentation.IActivityTemplateFactory>. L'interface dispose d'une seule méthode <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> avec laquelle vous pouvez créer et configurer les instances d'activité utilisées dans le modèle.

## <a name="to-create-a-template-for-the-delay-activity"></a>Pour créer un modèle pour l'activité Delay

1. Démarrez Visual Studio 2010.

2. Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3. Dans le **Types de projets** volet, sélectionnez **Workflow** à partir de le le **Visual C#** projets ou **Visual Basic** regroupements en fonction de votre langue de préférence.

4. Dans le **modèles** volet, sélectionnez **bibliothèque d’activités**.

5. Dans le **nom** , entrez `DelayActivityTemplate`.

6. Acceptez les valeurs par défaut dans le **emplacement** et **nom de la Solution** zones de texte, puis cliquez sur **OK**.

7. Cliquez sur le répertoire References du projet DelayActivityTemplate dans **l’Explorateur de solutions** et choisissez **ajouter une référence** pour ouvrir le **ajouter une référence** boîte de dialogue.

8. Accédez à la **.NET** onglet et sélectionnez **PresentationFramework** à partir de la **nom du composant** colonne sur la gauche, puis sur **OK** pour ajouter une référence dans le fichier PresentationFramework.dll.

9. Répétez cette procédure pour ajouter des références aux fichiers System.Activities.Presentation.dll et WindowsBase.dll.

10. Cliquez sur le projet DelayActivityTemplate dans **l’Explorateur de solutions** et choisissez **ajouter** , puis **un nouvel élément** pour ouvrir le **ajouter un nouvel élément**boîte de dialogue.

11. Sélectionnez le **classe** modèle, nommez-le MyDelayTemplate, puis cliquez sur **OK**.

12. Ouvrez le fichier MyDelayTemplate.cs et ajoutez les instructions suivantes.

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implémentez <xref:System.Activities.Presentation.IActivityTemplateFactory> avec la classe `MyDelayActivity` dans le code suivant. Cela configure une durée de 10 secondes comme délai.

    ```
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

14. Sélectionnez **générer la Solution** à partir de la **Build** menu pour générer le fichier DelayActivityTemplate.dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Pour rendre le modèle disponible dans un concepteur de workflow

1. Avec le bouton droit de la solution DelayActivityTemplate dans **l’Explorateur de solutions** et choisissez **ajouter** , puis **nouveau projet** pour ouvrir le **ajouter un nouveau projet** boîte de dialogue.

2. Sélectionnez le **Application Console de Workflow** modèle, nommez-le `CustomActivityTemplateApp`, puis cliquez sur **OK**.

3. Cliquez sur le répertoire References du projet CustomActivityTemplateApp dans **l’Explorateur de solutions** et choisissez **ajouter une référence** pour ouvrir le **ajouter une référence** boîte de dialogue zone.

4. Accédez à la **projets** onglet et sélectionnez **DelayActivityTemplate** à partir de la **nom_projet** colonne sur la gauche, puis sur **OK** pour ajouter un faire référence au fichier DelayActivityTemplate.dll que vous avez créé dans la première procédure.

5. Cliquez sur le projet CustomActivityTemplateApp dans **l’Explorateur de solutions** et choisissez **Build** pour compiler l’application.

6. Cliquez sur le projet CustomActivityTemplateApp dans **l’Explorateur de solutions** et choisissez **définir comme projet de démarrage**.

7. Sélectionnez **démarrer sans débogage** à partir de la **déboguer** menu, puis appuyez sur une touche pour continuer lorsque vous êtes invité à partir de la fenêtre cmd.exe.

8. Ouvrez le fichier Workflow1.xaml et ouvrez le **boîte à outils**.

9. Recherchez le **MyDelayActivity** modèle dans le **DelayActivityTemplate** catégorie. Faites-le glisser vers l'aire de conception. Vérifiez dans le **propriétés** fenêtre qui le `Duration` propriété a été définie sur 10 secondes.

## <a name="example"></a>Exemple
 Le fichier MyDelayActivity.cs doit contenir le code suivant.

```
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
- [Personnalisation de l’expérience de conception de workflow](customizing-the-workflow-design-experience.md)
