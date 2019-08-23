---
title: 'Procédure pas à pas : création d’un contrôle composite avec Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: cb54ef372e6da551b95f1edf61e3844b9dcba4c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950038"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Procédure pas à pas : création d’un contrôle composite avec Visual Basic
Les contrôles composites permettent de créer et de réutiliser des interfaces graphiques personnalisées. Un contrôle composite est avant tout un composant doté d’une représentation visuelle. Par conséquent, il peut comporter un ou plusieurs blocs de code, composants ou contrôles Windows Forms qui peuvent en étendre les fonctionnalités en validant les entrées d’utilisateur, en modifiant les propriétés d’affichage ou en effectuant d’autres tâches requises par l’auteur. Les contrôles composites peuvent être insérés dans les Windows Forms de la même manière que les autres contrôles. Dans la première partie de cette procédure pas à pas, vous allez créer un contrôle composite simple appelé `ctlClock`. Dans la seconde partie de la procédure pas à pas, vous allez étendre les fonctionnalités de `ctlClock` via l’héritage.

## <a name="creating-the-project"></a>Création du projet
 Lorsque vous créez un nouveau projet, vous spécifiez son nom pour définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock

1. Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

2. Dans la liste des projets Visual Basic, sélectionnez le modèle de projet **bibliothèque de contrôles Windows** , tapez `ctlClockLib` dans la zone **nom** , puis cliquez sur **OK**.

     Le nom du projet, `ctlClockLib`, est également assigné à l’espace de noms racine par défaut. L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly. Par exemple, si deux assemblies contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l’aide de `ctlClockLib.ctlClock.`.

3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **UserControl1.vb**, puis cliquez sur **Renommer**. Remplacez le nom de fichier par `ctlClock.vb`. Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».

    > [!NOTE]
    > Par défaut, un contrôle composite hérite de <xref:System.Windows.Forms.UserControl> la classe fournie par le système. La <xref:System.Windows.Forms.UserControl> classe fournit les fonctionnalités requises par tous les contrôles composites et implémente les méthodes et les propriétés standard.

4. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Ajout de composants et de contrôles Windows au contrôle composite
 L’interface visuelle est un composant essentiel de votre contrôle composite. Cette interface visuelle est implémentée par l’ajout d’un ou de plusieurs contrôles Windows sur l’aire du concepteur. Dans la démonstration suivante, vous allez intégrer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter des fonctionnalités.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Pour ajouter une étiquette et une minuterie à votre contrôle composite

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Concepteur de vues**.

2. Dans la boîte à outils, développez le nœud **Contrôles communs**, puis double-cliquez sur **Étiquette**.

     Un <xref:System.Windows.Forms.Label> contrôle nommé `Label1` est ajouté à votre contrôle sur l’aire du concepteur.

3. Dans le concepteur, cliquez sur **Label1**. Dans la fenêtre Propriétés, définissez les propriétés suivantes.

    |Propriété|Remplacer par|
    |--------------|---------------|
    |**Name**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. Dans la **boîte à outils**, développez le nœud **Composants**, puis double-cliquez sur **Minuterie**.

     Comme un <xref:System.Windows.Forms.Timer> est un composant, il n’a pas de représentation visuelle au moment de l’exécution. Par conséquent, il n’apparaît pas avec les contrôles sur l’aire du concepteur, mais plutôt dans le Concepteur de composants (une barre d’état située en bas de l’aire du concepteur).

5. Dans le concepteur de composants, cliquez sur **Timer1**, puis affectez à `1000` la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la <xref:System.Windows.Forms.Timer.Interval%2A> valeur `True`et à la propriété la valeur.

     La <xref:System.Windows.Forms.Timer.Interval%2A> propriété contrôle la fréquence à laquelle le composant Timer est en graduation. À chaque nouvelle graduation du composant `Timer1`, le code est exécuté dans l’événement `Timer1_Tick`. L’intervalle représente le nombre de millisecondes entre les graduations.

6. Dans le Concepteur de composants, double-cliquez sur **Timer1** pour accéder à l’événement `Timer1_Tick` pour `ctlClock`.

7. Modifiez le code afin qu’il ressemble à l’exemple de code suivant. Remplacez le paramètre de modificateur d’accès `Private` par `Protected`.

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     Ce code entraînera l’affichage de l’heure actuelle dans `lblDisplay`. Étant donné que l’intervalle du composant `Timer1` a été défini sur `1000`, cet événement se produira toutes les mille millisecondes, mettant ainsi l’heure à jour toutes les secondes.

8. Modifiez la méthode afin qu’elle soit remplaçable. Pour plus d’informations, consultez la section « Héritage d’un contrôle utilisateur » ci-dessous.

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="adding-properties-to-the-composite-control"></a>Ajout de propriétés au contrôle composite
 Votre contrôle Clock encapsule maintenant un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.Timer> composant, chacun avec son propre ensemble de propriétés inhérentes. Même si les propriétés individuelles de ces contrôles ne seront pas accessibles aux autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés. Dans la procédure suivante, vous allez ajouter des propriétés à votre contrôle qui permettent à l’utilisateur de modifier la couleur de l’arrière-plan et du texte.

### <a name="to-add-a-property-to-your-composite-control"></a>Pour ajouter une propriété à votre contrôle composite

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Afficher le code**.

     L’éditeur de code de votre contrôle s’ouvre.

2. Recherchez l’instruction `Public Class ctlClock`. Sous l’instruction, saisissez le code suivant.

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous allez créer.

3. Insérez le code suivant sous les déclarations de variable de l’étape 2.

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     Le code précédent crée deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, auxquelles les autres utilisateurs du contrôle pourront accéder en appelant l’instruction `Property`. `Get` et `Set` fournissent des instructions pour le stockage et la récupération de la valeur de propriété, ainsi que le code pour intégrer les fonctionnalités appropriées à la propriété.

4. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="testing-the-control"></a>Test du contrôle
 Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur. Testez le comportement de votre contrôle au moment de l’exécution et testez ses propriétés avec le **Conteneur de test UserControl**. Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.

### <a name="to-test-your-control"></a>Pour tester votre contrôle

1. Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.

2. Dans la grille des propriétés du conteneur de test, sélectionnez la propriété `ClockBackColor`, puis cliquez sur la flèche déroulante pour afficher la palette de couleurs.

3. Choisissez une couleur en cliquant dessus.

     La couleur sélectionnée devient la couleur d’arrière-plan de votre contrôle.

4. Utilisez une séquence d’événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.

5. Cliquez sur **Fermer** pour fermer le **Conteneur de test UserControl**.

     Dans cette section et les sections précédentes, vous avez vu comment les composants et contrôles Windows peuvent être combinés avec du code et de l’empaquetage afin d’offrir des fonctionnalités personnalisées sous la forme d’un contrôle composite. Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester votre contrôle après sa configuration. Dans la section suivante, vous allez apprendre à créer un contrôle composite hérité en utilisant `ctlClock` comme base.

## <a name="inheriting-from-a-composite-control"></a>Héritage d’un contrôle composite
 Dans les sections précédentes, vous avez appris à combiner du code, des composants et des contrôles Windows pour créer des contrôles composites réutilisables. Votre contrôle composite peut maintenant être utilisé comme base pour créer d’autres contrôles. Le processus qui consiste à créer une classe à partir d’une classe de base est appelé *héritage*. Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`. Ce contrôle sera créé à partir de son contrôle parent, `ctlClock`. Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en remplaçant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.

 La première étape de la création d’un contrôle hérité consiste à le dériver de son parent. Cette action crée un contrôle qui possède toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également être utilisé comme base pour l’ajout de fonctionnalités nouvelles ou modifiées.

### <a name="to-create-the-inherited-control"></a>Pour créer le contrôle hérité

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, pointez sur **Ajouter**, puis cliquez sur **Contrôle utilisateur**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Sélectionnez le modèle **Contrôle utilisateur hérité**.

3. Dans le champ **Nom**, saisissez `ctlAlarmClock.vb`, puis cliquez sur **Ajouter**.

     La boîte de dialogue **Sélecteur d’héritage** s’affiche.

4. Sous **Nom du composant**, double-cliquez sur **ctlClock**.

5. Dans l’Explorateur de solutions, parcourez les projets en cours.

    > [!NOTE]
    > Un fichier appelé **ctlAlarmClock.vb** a été ajouté au projet actuel.

### <a name="adding-the-alarm-properties"></a>Ajout de propriétés d’alarme
 Les propriétés sont ajoutées à un contrôle hérité de la même façon qu’elles sont ajoutées à un contrôle composite. Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la date et l’heure de désactivation de l’alarme, et `AlarmSet`, qui indique si oui ou non l’alarme est définie.

#### <a name="to-add-properties-to-your-composite-control"></a>Pour ajouter des propriétés à votre contrôle composite

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Afficher le code**.

2. Recherchez la déclaration de classe pour le contrôle ctlAlarmClock qui apparaît sous la forme `Public Class ctlAlarmClock`.  Dans la déclaration de classe, insérez le code suivant.

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a>Ajout de l’interface graphique du contrôle
 Votre contrôle hérité possède une interface visuelle qui est identique à celle du contrôle dont il a hérité. Il possède les mêmes contrôles constitutifs que son contrôle parent, mais les propriétés de ces contrôles ne seront pas disponibles, sauf si elles ont été spécifiquement exposées. Vous pouvez ajouter des éléments à l’interface graphique d’un contrôle composite hérité de la même manière que vous ajoutez des éléments à tout autre contrôle composite. Pour continuer à ajouter des éléments à l’interface visuelle de votre alarme, vous allez ajouter un contrôle Étiquette qui clignote lorsque l’alarme sonne.

#### <a name="to-add-the-label-control"></a>Pour ajouter le contrôle Étiquette

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Concepteur de vues**.

     Le concepteur pour `ctlAlarmClock` s’ouvre dans la fenêtre principale.

2. Cliquez sur `lblDisplay` (la partie visible du contrôle) et affichez la fenêtre Propriétés.

    > [!NOTE]
    > Toutes les propriétés qui s’affichent sont grisées. Cela indique que ces propriétés sont propres à `lblDisplay` et ne peuvent pas être modifiées ou sélectionnées dans la fenêtre Propriétés. Par défaut, les contrôles contenus dans un contrôle composite sont à l’état `Private`, et leurs propriétés ne sont accessibles d’aucune façon.

    > [!NOTE]
    > Si vous souhaitez que d’autres utilisateurs de votre contrôle composite puissent accéder à ses contrôles internes, définissez leur état sur `Public` ou `Protected`. Cela vous permettra de définir et de modifier les propriétés des contrôles contenus dans votre contrôle composite à l’aide du code approprié.

3. Ajoutez un <xref:System.Windows.Forms.Label> contrôle à votre contrôle composite.

4. À l’aide de la souris <xref:System.Windows.Forms.Label> , faites glisser le contrôle immédiatement en dessous de la zone d’affichage. Dans la fenêtre Propriétés, définissez les propriétés suivantes.

    |Propriété|Paramètre|
    |--------------|-------------|
    |**Name**|`lblAlarm`|
    |**Text**|**Alarm!**|
    |**TextAlign**|`MiddleCenter`|
    |**Visible**|`False`|

### <a name="adding-the-alarm-functionality"></a>Ajout de la fonctionnalité d’alarme
 Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle permettant d’activer la fonctionnalité d’alarme dans votre contrôle composite. Dans cette procédure, vous allez ajouter du code pour comparer l’heure actuelle à l’heure de l’alarme et, si elles sont identiques, déclencher le son et le clignotement de l’alarme. En remplaçant la méthode `Timer1_Tick` de `ctlClock` et en lui ajoutant du code, vous allez étendre les capacités de `ctlAlarmClock` tout en conservant les fonctionnalités inhérentes de `ctlClock`.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Pour remplacer la méthode Timer1_Tick de ctlClock

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Afficher le code**.

2. Recherchez l’instruction `Private blnAlarmSet As Boolean`. Juste en dessous de l’instruction, ajoutez l’instruction suivante.

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. Recherchez l’instruction `End Class` au bas de la page. Juste avant l’instruction `End Class`, ajoutez le code suivant.

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     L’ajout de ce code permet d’effectuer plusieurs tâches. L’instruction `Overrides` ordonne au contrôle d’utiliser cette méthode à la place de la méthode héritée du contrôle de base. Lorsque cette méthode est appelée, elle appelle la méthode qu’elle remplace en appelant l’instruction `MyBase.Timer1_Tick`, ce qui permet de s’assurer que toutes les fonctionnalités intégrées au contrôle d’origine sont également intégrées à ce contrôle. Du code supplémentaire est ensuite exécuté pour intégrer la fonctionnalité d’alarme. Lorsque l’alarme se déclenche, un contrôle Étiquette clignotant apparaît et un signal sonore retentit.

    > [!NOTE]
    > Comme vous remplacez un gestionnaire d’événements hérité, il n’est pas nécessaire de spécifier l’événement avec le mot clé `Handles`. L’événement est déjà rattaché. Tout ce que vous remplacez est l’implémentation du gestionnaire.

     Votre contrôle d’alarme est presque terminé. La seule chose qui reste à faire est de mettre en place un moyen de le désactiver. Pour ce faire, vous allez ajouter du code à la méthode `lblAlarm_Click`.

#### <a name="to-implement-the-shutoff-method"></a>Pour implémenter la méthode de désactivation

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Concepteur de vues**.

2. Dans le concepteur, double-cliquez sur **lblAlarm**. **L’éditeur de code** s’ouvre à la ligne `Private Sub lblAlarm_Click`.

3. Modifiez cette méthode afin qu’elle ressemble au code suivant.

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

### <a name="using-the-inherited-control-on-a-form"></a>Utilisation du contrôle hérité sur un formulaire
 Vous pouvez tester votre contrôle hérité de la même façon que vous avez testé le contrôle `ctlClock`de classe de base,: Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**. Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.

 Pour pouvoir utiliser votre contrôle, vous devrez l’héberger dans un formulaire. À l’instar d’un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de manière autonome et doit être hébergé dans un formulaire ou un autre conteneur. Étant donné que `ctlAlarmClock` présente davantage de fonctionnalités, du code supplémentaire est nécessaire pour le tester. Dans cette procédure, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`. Vous allez écrire du code pour définir et afficher la propriété `AlarmTime` de `ctlAlarmClock`, puis vous testerez ses fonctions inhérentes.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Pour générer votre contrôle et l’ajouter à un formulaire de test

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, puis cliquez sur **Générer**.

2. Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.

3. Ajoutez un nouveau projet **d’application Windows** à la solution et nommez-le `Test`.

     Le projet **Test** est ajouté à l’Explorateur de solutions.

4. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet `Test`, puis cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.

5. Cliquez sur l’onglet intitulé **Projets**. Le projet **ctlClockLib** s’affiche sous **Nom du projet**. Double-cliquez sur **ctlClockLib** pour ajouter la référence au projet de test.

6. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Générer**.

7. Dans la **boîte à outils**, développez le nœud **Composants ctlClockLib**.

8. Double-cliquez sur **ctlAlarmClock** pour ajouter une instance de `ctlAlarmClock` à votre formulaire.

9. Dans la **boîte à outils**, recherchez et double -cliquez sur DateTimePicker <xref:System.Windows.Forms.DateTimePicker> pour ajouter un contrôle à votre formulaire, puis <xref:System.Windows.Forms.Label> ajoutez un contrôle en double-cliquant sur **étiquette**.

10. Utilisez la souris pour positionner les contrôles à un endroit approprié sur le formulaire.

11. Définissez les propriétés de ces contrôles de la manière suivante.

    |Contrôle|Propriété|Value|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**Name**|`lblTest`|
    |`dateTimePicker1`|**Name**|`dtpTest`|
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. Dans le concepteur, double-cliquez sur **dtpTest**.

     **L’éditeur de code** s’ouvre à la ligne `Private Sub dtpTest_ValueChanged`.

13. Modifiez le code afin qu’il ressemble à l’exemple de code suivant.

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Définir comme projet de démarrage**.

15. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.

     Le programme de test démarre. Notez que l’heure actuelle est mise à jour `ctlAlarmClock` dans le contrôle et que l’heure de début est affichée <xref:System.Windows.Forms.DateTimePicker> dans le contrôle.

16. Cliquez sur <xref:System.Windows.Forms.DateTimePicker> l’emplacement où les minutes de l’heure sont affichées.

17. À l’aide du clavier, définissez une valeur pour les minutes comportant une minute de plus que l’heure actuelle affichée par `ctlAlarmClock`.

     L’heure de déclenchement de l’alarme apparaît dans `lblTest`. Attendez que l’heure affichée atteigne l’heure de déclenchement de l’alarme. Lorsque l’heure affichée atteint l’heure sur laquelle l’alarme a été définie, un signal sonore retentit et `lblAlarm` se met à clignoter.

18. Désactivez l’alarme en cliquant sur `lblAlarm`. Vous pouvez maintenant réinitialiser l’alarme.

     Cette procédure pas à pas a abordé plusieurs concepts clés. Vous avez appris à créer un contrôle composite en combinant des contrôles et des composants dans un conteneur de contrôle composite. Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code pour implémenter des fonctionnalités personnalisées. Dans la dernière section, vous avez appris à étendre les fonctionnalités d’un contrôle composite grâce à l’héritage et à modifier les fonctionnalités des méthodes hôtes en remplaçant ces méthodes.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Guide pratique pour Créer des contrôles composites](how-to-author-composite-controls.md)
- [Guide pratique pour Afficher un contrôle dans la boîte de dialogue choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
