---
title: External RuleSet Toolkit
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: eb59b02d469788b23126f4e02c5b7ae5a63081f0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094668"
---
# <a name="external-ruleset-toolkit"></a>External RuleSet Toolkit

Généralement, lorsque des règles sont utilisées dans une application de workflow, elles font partie de l'assembly. Dans certains cas, il peut être préférable de gérer les RuleSets séparément de l'assembly afin qu'ils soient mis à jour sans que la génération et le déploiement de l'assembly de workflow ne soient nécessaires. Cet exemple vous permet de gérer et de modifier des RuleSets dans une base de données et d'accéder à ceux-ci à partir d'un workflow au moment de son exécution, opération qui permet aux instances de workflow en cours d'intégrer automatiquement des modifications de RuleSets.

L'exemple External RuleSet Toolkit contient un utilitaire basé sur les Windows Forms pouvant être utilisé pour gérer et modifier les versions d'un RuleSet dans une base de données. Il inclut également une activité et un service hôte permettant d'exécuter ces règles.

> [!NOTE]
> Cet exemple requiert [Microsoft SQL Server](/sql).

Visual Studio fournit un éditeur de groupe de règles dans le cadre de l’Windows Workflow Foundation (WF). Vous pouvez démarrer cet éditeur en double-cliquant sur l'activité `Policy` dans un workflow ; cette opération sérialise l'objet RuleSet défini au fichier .rules associé au workflow (une activité `Policy` exécute une instance RuleSet sur le workflow). Le fichier .rules est compilé dans l'assembly en tant que ressource lors de la génération du projet de workflow.

Les composants de cet exemple incluent les éléments suivants :

- Un outil GUI RuleSet pouvant être utilisé pour modifier et gérer des versions de RuleSets dans la base de données.

- Un service de RuleSet configuré dans l'application hôte et accédant aux RuleSets de la base de données.

- Une activité `ExternalPolicy` nécessitant un RuleSet du service de RuleSet et exécutant ce RuleSet sur le workflow.

L’interaction des composants est illustrée dans l’image suivante. Les sections qui suivent décrivent chacun de ces composants.

![Diagramme montrant la vue d’ensemble de l’exemple External RuleSet Toolkit.](./media/external-ruleset-toolkit/ruleset-toolkit-overview.gif)

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`

## <a name="ruleset-tool"></a>Outil RuleSet

L’image suivante est une capture d’écran de l’outil RuleSet. Dans le menu **magasin de règles** , vous pouvez charger les ensembles de règles disponibles à partir de la base de données et enregistrer les ensembles de règles modifiés dans le magasin. Un fichier de configuration d'application contient une chaîne de connexion pour la base de données RuleSet. Lorsque vous démarrez l'outil, ce dernier charge automatiquement les RuleSets à partir de la base de données configurée.

![Capture d’écran montrant le navigateur de l’ensemble de règles.](./media/external-ruleset-toolkit/ruleset-browser-dialog.gif)

L’outil RuleSet applique aux RuleSets des numéros de version principaux et secondaires, vous permettant de gérer et de stocker simultanément plusieurs versions. Il ne dispose pas de fonctionnalités de verrouillage ou de contrôle de configuration en plus de ces fonctionnalités de versions. Cet outil vous permet de créer des versions de RuleSets ou de supprimer des versions existantes. Lorsque vous cliquez sur **nouveau**, l’outil crée un nouveau nom d’ensemble de règles et applique la version 1,0. Lorsque vous copiez une version, l'outil crée une copie de la version de l'ensemble de règles sélectionné, y compris les règles qu'il contient, et assigne de nouveaux numéros de version uniques. Ces numéros sont basés sur ceux de RuleSets existants. Vous pouvez changer le nom d'un RuleSet et ses numéros de version en utilisant les champs associés sur le formulaire.

Lorsque vous cliquez sur **modifier les règles**, l’éditeur de RuleSet démarre, comme illustré dans l’image suivante :

![Capture d’écran montrant l’éditeur de RuleSet.](./media/external-ruleset-toolkit/ruleset-editor-dialog.gif)

Il s’agit d’un nouvel hébergement de la boîte de dialogue de l’éditeur qui fait partie du complément Windows Workflow Foundation Visual Studio. Elle contient les mêmes fonctionnalités, y compris la prise en charge Intellisense. Les règles sont créées par rapport à un type de cible (tel qu’un flux de travail) associé au RuleSet dans l’outil. Lorsque vous cliquez sur **Parcourir** dans la boîte de dialogue principale de l’outil, la boîte de dialogue **Workflow/Type Selector** s’affiche, comme illustré à la figure 4.

![Sélection &#47;du type de workflow](./media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")

Figure 4 : Workflow/Type Selector

Vous pouvez utiliser la boîte de dialogue **du sélecteur de flux de travail/type** pour spécifier un assembly et un type spécifique au sein de cet assembly. Ce type correspond au type de cible pour lequel les règles sont créées (et exécutées). Dans de nombreux cas, le type de cible est un workflow ou un autre type d'activité. Toutefois, il est possible d'exécuter un RuleSet sur tout type .NET.

Le chemin d’accès au fichier d’assembly et le type `name are stored with the` ensemble de règles dans la base de données, de sorte que lorsque le RuleSet est récupéré de la base de données, l’outil tente de charger automatiquement le type cible.

Lorsque vous cliquez sur **OK** dans la boîte de dialogue du **Sélecteur de flux de travail/type** , il valide le type sélectionné par rapport à l’ensemble de règles, afin de garantir que tous les membres sont référencés par les règles dans le type cible. Les erreurs sont affichées dans une boîte de dialogue **Erreurs de validation** . Vous pouvez choisir de poursuivre la modification en dépit des erreurs, ou de cliquer sur **Annuler**. Dans le menu **Outils** de la boîte de dialogue principale de l’outil, vous pouvez cliquer sur **valider** pour revalider la version de l’ensemble de règles par rapport à l’activité cible.

![Capture d’écran montrant la boîte de dialogue Erreurs de validation.](./media/external-ruleset-toolkit/validation-errors-dialog.png)

Dans le menu **données** de l’outil, vous pouvez importer et exporter des ensembles de règles. Lorsque vous cliquez sur **Importer**, une boîte de dialogue de sélection de fichier s’affiche, à partir de laquelle vous pouvez sélectionner un fichier. Rules. Il se peut qu’il soit ou non un fichier initialement créé dans Visual Studio. Le fichier .rules doit contenir une instance de `RuleDefinitions` sérialisée qui dispose d’une collection de conditions et d’une collection de RuleSets. L’outil n’utilise pas la collection de conditions, mais il utilise le format `RuleDefinitions`. Rules pour permettre l’interaction avec l’environnement Visual Studio.

Une fois que vous avez sélectionné un fichier. Rules, une boîte de dialogue de **sélection de RuleSet** s’affiche. Celle-ci permet de sélectionner les ensembles de règles que vous souhaitez importer à partir du fichier (par défaut, tous les ensembles de règles sont sélectionnés). Les RuleSets d'un fichier .rules ne disposent pas de numéros de version, car leur version dans un projet WF est identique à celle de l'assembly. Pendant le processus d’importation, l’outil attribue automatiquement le numéro de version principale disponible suivant (que vous pouvez modifier après l’importation). vous pouvez voir les numéros de version attribués dans la liste du **Sélecteur RuleSet** .

Pour chaque RuleSet importé, l’outil tente de localiser le type associé dans le dossier bin\Debug qui se trouve sous l’emplacement du fichier .rules (s’il existe), en fonction des membres utilisés dans le RuleSet. Si l'outil détecte plusieurs types correspondants, il essaie d'en choisir un en fonction d'une correspondance entre le nom de fichier .rules et celui du type (par exemple, le type `Workflow1` correspond au fichier Workflow1.rules). Si plusieurs noms concordent, vous êtes invité à sélectionner le type. Si ce mécanisme d’identification automatique ne parvient pas à localiser un assembly ou un type correspondant, après l’importation, vous pouvez cliquer sur **Parcourir** dans la boîte de dialogue principale de l’outil pour accéder au type associé. L’illustration suivante montre le sélecteur de RuleSet :

![Capture d’écran montrant la boîte de dialogue du sélecteur de RuleSet.](./media/external-ruleset-toolkit/ruleset-selector-dialog.gif)

Lorsque vous cliquez sur **Data-Export** dans le menu principal de l’outil, la boîte de dialogue **RuleSet Selector** s’affiche à nouveau, à partir de laquelle vous pouvez déterminer les ensembles de règles de la base de données qui doit être exportée. Lorsque vous cliquez sur **OK**, une boîte de dialogue **enregistrer le fichier** s’affiche, dans laquelle vous pouvez spécifier le nom et l’emplacement du fichier. Rules résultant. Le fichier .rules ne contenant aucune information sur la version, vous pouvez sélectionner une seule version de RuleSet répondant à un nom donné.

## <a name="policyfromservice-activity"></a>Activité PolicyFromService

Le code correspondant à l'activité `PolicyFromService` est très simple. Il fonctionne exactement comme l'activité `Policy` fournie avec WF, mais au lieu de récupérer le RuleSet cible dans le fichier .rules, il appelle un service hôte pour obtenir l'instance de ce RuleSet. Il exécute ensuite le RuleSet sur l'instance de l'activité du workflow racine.

Pour utiliser l'activité dans un workflow, ajoutez une référence aux assemblys `PolicyActivities` et `RuleSetService` de votre projet de workflow. Consultez la procédure située à la fin de cette rubrique pour savoir comment ajouter une activité à la boîte à outils.

Après avoir ajouté l'activité à votre workflow, vous devez indiquer le nom du RuleSet à exécuter. Vous pouvez indiquer ce nom en tant que valeur littérale ou le lier à la variable ou à la propriété de workflow d'une autre activité. Vous pouvez également indiquer des numéros de version pour le RuleSet à exécuter (facultatif). Si vous laissez la valeur par défaut (0) comme numéro de version principal ou secondaire, le numéro de version le plus récent figurant dans la base de données sera automatiquement assigné à l'activité.

## <a name="ruleset-service"></a>Service de RuleSet

Ce service est chargé de récupérer dans la base de données la version indiquée du RuleSet et de la renvoyer à l'activité appelante. Comme indiqué précédemment, si la valeur des versions principales et secondaires passées dans l'appel `GetRuleSet` est de 0, le service récupère la version la plus récente. À ce stade, aucune mise en cache des définitions ou des instances de RuleSets n’est effectuée ; de la même façon, aucune fonctionnalité visant à marquer certaines versions de RuleSets comme étant « déployées » (afin de les différencier des RuleSets en cours) n’est appliquée.

La base de données devant être consultée par le service doit être configurée sur l'hôte à l'aide d'un fichier de configuration d'application.

#### <a name="to-run-the-tool"></a>Pour exécuter l'outil

1. Le dossier de configuration de la table RuleSet utilisée par l’outil et par le service contient un fichier Setup.sql. Vous pouvez exécuter le fichier de commandes Setup.cmd pour créer la base de données Rules dans SQL Express et configurer la table RuleSet.

2. Si vous modifiez le fichier de commandes ou Setup.sql et indiquez de ne pas utiliser SQL Express ou d'ajouter la table dans une base de données autre que `Rules`, les fichiers de configuration d'application de l'outil RuleSet et les projets `UsageSample` doivent être modifiés pour contenir les mêmes informations.

3. Après avoir exécuté le script Setup.sql, vous pouvez générer la solution `ExternalRuleSetToolkit` puis exécuter l'outil RuleSet à partir du projet ExternalRuleSetTool.

4. La solution `RuleSetToolkitUsageSample` Sequential Workflow Console Application contient un exemple de workflow. Ce dernier se compose d'une activité `PolicyFromService` et de deux variables (`orderValue` et `discount`) sur lesquelles le RuleSet cible s'exécute.

5. Pour utiliser cet exemple, générez la solution `RuleSetToolkitUsageSample`. Ensuite, dans le menu principal de l’outil RuleSet, cliquez sur **Data-Import** et pointez sur le fichier DiscountRuleSet. Rules dans le dossier RuleSetToolkitUsageSample. Cliquez sur l’option de menu **enregistrer le magasin de règles** pour enregistrer l’ensemble de règles importé dans la base de données.

6. L'assembly `PolicyActivities` étant référencé à partir du projet de workflow exemple, l'activité `PolicyFromService` apparaît dans le workflow. Toutefois, elle ne s'affiche pas par défaut dans la boîte à outils. Pour l'ajouter à la boîte à outils, procédez comme suit :

    - Cliquez avec le bouton droit sur la boîte à outils et sélectionnez **choisir les éléments** (cette opération peut prendre un certain temps).

    - Quand la boîte de dialogue **choisir des éléments de boîte à outils** s’affiche, cliquez sur l’onglet **activités** .

    - Accédez à l’assembly `PolicyActivities` dans la solution `ExternalRuleSetToolkit`, puis cliquez sur **ouvrir**.

    - Assurez-vous que l’activité `PolicyFromService` est sélectionnée dans la boîte de dialogue **choisir des éléments de boîte à outils** , puis cliquez sur **OK**.

    - L’activité doit maintenant apparaître dans la boîte à outils de la catégorie **composants RuleSetToolkitUsageSample** .

7. Le service de RuleSet est déjà configuré dans l'application console hôte via l'instruction suivante dans Program.cs.

    ```csharp
    workflowRuntime.AddService(new RuleSetService());
    ```

8. Vous pouvez également configurer le service sur l'hôte en utilisant un fichier de configuration ; consultez la documentation du kit de développement logiciel (SDK) pour plus de détails.

9. Un fichier de configuration d'application est ajouté au projet de workflow afin d'indiquer la chaîne de connexion correspondant à la base de données devant être utilisée par le service. Cette chaîne doit être la même que celle utilisée par l'outil RuleSet, laquelle cible la base de données contenant la table RuleSet.

10. Vous pouvez désormais exécuter le projet `RuleSetToolkitUsageSample` comme s'il s'agissait de toute autre application console de workflow. Appuyez sur F5 ou sur CTRL + F5 dans Visual Studio ou exécutez le fichier RuleSetToolkitUsageSample. exe directement.

    > [!NOTE]
    > Vous devez fermer l'outil RuleSet pour recompiler l'exemple d'utilisation, car l'outil charge l'assembly correspondant à cet exemple.
