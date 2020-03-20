---
title: "Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#"
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546722"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Procédure pas à pas: Auteur d’un contrôle composite avec C\#

Les contrôles composites permettent de créer et de réutiliser des interfaces graphiques personnalisées. Un contrôle composite est avant tout un composant doté d’une représentation visuelle. Par conséquent, il peut comporter un ou plusieurs blocs de code, composants ou contrôles Windows Forms qui peuvent en étendre les fonctionnalités en validant les entrées d’utilisateur, en modifiant les propriétés d’affichage ou en effectuant d’autres tâches requises par l’auteur. Les contrôles composites peuvent être insérés dans les Windows Forms de la même manière que les autres contrôles. Dans la première partie de cette procédure pas à pas, vous allez créer un contrôle composite simple appelé `ctlClock`. Dans la seconde partie de la procédure pas à pas, vous allez étendre les fonctionnalités de `ctlClock` via l’héritage.

## <a name="create-the-project"></a>Création du projet

Lorsque vous créez un nouveau projet, vous spécifiez son nom pour définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock

1. Dans Visual Studio, créez un nouveau projet **de bibliothèque de contrôle des formulaires Windows** et nommez-le **ctlClockLib**.

     Le nom du projet, `ctlClockLib`, est également assigné à l’espace de noms racine par défaut. L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly. Par exemple, si deux assemblies contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l’aide de `ctlClockLib.ctlClock.`.

2. Dans **Solution Explorer**, cliquez à droite **UserControl1.cs**, puis cliquez sur **Rename**. Remplacez le nom de fichier par `ctlClock.cs`. Cliquez sur le bouton **Oui** lorsqu’on vous demande si vous souhaitez renommer toutes les références à l’élément code "UserControl1".

    > [!NOTE]
    > Par défaut, un contrôle composite <xref:System.Windows.Forms.UserControl> hérite de la classe fournie par le système. La <xref:System.Windows.Forms.UserControl> classe fournit les fonctionnalités requises par tous les contrôles composites, et implémente les méthodes et les propriétés standard.

3. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Ajouter les commandes et les composants Windows au contrôle composite

L’interface visuelle est un composant essentiel de votre contrôle composite. Cette interface visuelle est implémentée par l’ajout d’un ou de plusieurs contrôles Windows sur l’aire du concepteur. Dans la démonstration suivante, vous allez intégrer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter des fonctionnalités.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Pour ajouter une étiquette et une minuterie à votre contrôle composite

1. Dans **Solution Explorer**, clic droit **ctlClock.cs**, puis cliquez sur View **Designer**.

2. Dans la **boîte à outils**, étendre le nœud Common **Controls,** puis double clic **Label**.

     Un <xref:System.Windows.Forms.Label> contrôle `label1` nommé est ajouté à votre contrôle sur la surface du concepteur.

3. Dans le concepteur, cliquez sur **l’étiquette1**. Dans la fenêtre Propriétés, définissez les propriétés suivantes.

    |Propriété|Remplacer par|
    |--------------|---------------|
    |**Nom   **|`lblDisplay`|
    |**Texte**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. Dans la **boîte à outils**, développez le nœud **Composants**, puis double-cliquez sur **Minuterie**.

     Parce <xref:System.Windows.Forms.Timer> qu’un est un composant, il n’a pas de représentation visuelle au moment de l’exécution. Par conséquent, il n’apparaît pas avec les commandes sur la surface du concepteur, mais plutôt dans le **concepteur de composants** (un plateau au bas de la surface du concepteur).

5. Dans le **concepteur de composants**, cliquez sur `1000` <xref:System.Windows.Forms.Timer.Enabled%2A> **timer1**, puis définissez la <xref:System.Windows.Forms.Timer.Interval%2A> propriété à et la propriété à `true`.

     La <xref:System.Windows.Forms.Timer.Interval%2A> propriété contrôle la <xref:System.Windows.Forms.Timer> fréquence avec laquelle le composant tic-tac. À chaque nouvelle graduation du composant `timer1`, le code est exécuté dans l’événement `timer1_Tick`. L’intervalle représente le nombre de millisecondes entre les graduations.

6. Dans le **concepteur de composants**, minuterie à double **clic1** pour aller à l’événement `timer1_Tick` pour `ctlClock`.

7. Modifiez le code afin qu’il ressemble à l’exemple de code suivant. Remplacez le paramètre de modificateur d’accès `private` par `protected`.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Ce code entraînera l’affichage de l’heure actuelle dans `lblDisplay`. Étant donné que l’intervalle du composant `timer1` a été défini sur `1000`, cet événement se produira toutes les mille millisecondes, mettant ainsi l’heure à jour toutes les secondes.

8. Modifiez la méthode afin qu’elle soit remplaçable à l’aide du mot clé `virtual`. Pour plus d’informations, consultez la section « Héritage d’un contrôle utilisateur » ci-dessous.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="add-properties-to-the-composite-control"></a>Ajouter des propriétés au contrôle composite

Votre commande d’horloge encapsule maintenant un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.Timer> composant, chacun avec son propre ensemble de propriétés inhérentes. Même si les propriétés individuelles de ces contrôles ne seront pas accessibles aux autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés. Dans la procédure suivante, vous allez ajouter des propriétés à votre contrôle qui permettent à l’utilisateur de modifier la couleur de l’arrière-plan et du texte.

### <a name="to-add-a-property-to-your-composite-control"></a>Pour ajouter une propriété à votre contrôle composite

1. Dans **Solution Explorer**, cliquez à droite **ctlClock.cs**, puis cliquez sur Code **De vue**.

     **L’éditeur de code** pour votre contrôle s’ouvre.

2. Recherchez l’instruction `public partial class ctlClock`. Sous l’accolade ouvrante (`{)`, saisissez le code suivant.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous allez créer.

3. Entrez ou collez le code suivant sous les déclarations variables de l’étape 2.

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     Le code précédent crée deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, auxquelles les autres utilisateurs du contrôle pourront accéder. `get` et `set` fournissent des instructions pour le stockage et la récupération de la valeur de propriété, ainsi que le code pour intégrer les fonctionnalités appropriées à la propriété.

4. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

## <a name="test-the-control"></a>Tester le contrôle

Les contrôles ne sont pas des applications autonomes ; ils doivent être hébergés dans un conteneur. Testez le comportement de votre contrôle au moment de l’exécution et testez ses propriétés avec le **Conteneur de test UserControl**. Pour plus d’informations, consultez [Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Pour tester votre contrôle

1. Appuyez sur **F5** pour construire le projet et exécuter votre contrôle dans le **conteneur d’essai UserControl**.

2. Dans la grille des propriétés du conteneur de test, recherchez la propriété `ClockBackColor`, puis sélectionnez la propriété pour afficher la palette de couleurs.

3. Choisissez une couleur en cliquant dessus.

   La couleur sélectionnée devient la couleur d’arrière-plan de votre contrôle.

4. Utilisez une séquence d’événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.

   Dans cette section et les sections précédentes, vous avez vu comment les composants et contrôles Windows peuvent être combinés avec du code et de l’empaquetage afin d’offrir des fonctionnalités personnalisées sous la forme d’un contrôle composite. Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester votre contrôle après sa configuration. Dans la section suivante, vous allez apprendre à créer un contrôle composite hérité en utilisant `ctlClock` comme base.

## <a name="inherit-from-a-composite-control"></a>Hérite d’un contrôle composite

Dans les sections précédentes, vous avez appris à combiner du code, des composants et des contrôles Windows pour créer des contrôles composites réutilisables. Votre contrôle composite peut maintenant être utilisé comme base pour créer d’autres contrôles. Le processus qui consiste à créer une classe à partir d’une classe de base est appelé *héritage*. Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`. Ce contrôle sera créé à partir de son contrôle parent, `ctlClock`. Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en remplaçant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.

La première étape de la création d’un contrôle hérité consiste à le dériver de son parent. Cette action crée un contrôle qui possède toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également être utilisé comme base pour l’ajout de fonctionnalités nouvelles ou modifiées.

### <a name="to-create-the-inherited-control"></a>Pour créer le contrôle hérité

1. Dans **Solution Explorer**, clic droit **ctlClockLib**, pointez **ajouter**, puis cliquez sur contrôle **utilisateur**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Sélectionnez le modèle **Contrôle utilisateur hérité**.

3. Dans le champ **Nom**, saisissez `ctlAlarmClock.cs`, puis cliquez sur **Ajouter**.

     La boîte de dialogueSélecteur d’héritage s’affiche.

4. Sous **Nom du composant**, double-cliquez sur **ctlClock**.

5. Dans **Solution Explorer**, parcourez les projets en cours.

    > [!NOTE]
    > Un fichier appelé **ctlAlarmClock.cs** a été ajouté au projet actuel.

### <a name="add-the-alarm-properties"></a>Ajouter les propriétés Alarm

Les propriétés sont ajoutées à un contrôle hérité de la même façon qu’elles sont ajoutées à un contrôle composite. Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la date et l’heure de désactivation de l’alarme, et `AlarmSet`, qui indique si oui ou non l’alarme est définie.

#### <a name="to-add-properties-to-your-composite-control"></a>Pour ajouter des propriétés à votre contrôle composite

1. Dans **Solution Explorer**, clic droit **ctlAlarmClock**, puis cliquez sur **Code De vue**.

2. Recherchez l’instruction `public class`. Notez que votre contrôle hérite de `ctlClockLib.ctlClock`. Sous l’accolade ouvrante (`{)`, saisissez le code suivant.

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="add-to-the-graphical-interface-of-the-control"></a>Ajouter à l’interface graphique du contrôle

Votre contrôle hérité possède une interface visuelle qui est identique à celle du contrôle dont il a hérité. Il possède les mêmes contrôles constitutifs que son contrôle parent, mais les propriétés de ces contrôles ne seront pas disponibles, sauf si elles ont été spécifiquement exposées. Vous pouvez ajouter des éléments à l’interface graphique d’un contrôle composite hérité de la même manière que vous ajoutez des éléments à tout autre contrôle composite. Pour continuer à ajouter des éléments à l’interface visuelle de votre alarme, vous allez ajouter un contrôle Étiquette qui clignote lorsque l’alarme sonne.

#### <a name="to-add-the-label-control"></a>Pour ajouter le contrôle Étiquette

1. Dans **Solution Explorer**, clic droit **ctlAlarmClock**, puis cliquez sur View **Designer**.

     Le concepteur pour `ctlAlarmClock` s’ouvre dans la fenêtre principale.

2. Cliquez sur la partie visible du contrôle et affichez la fenêtre Propriétés.

    > [!NOTE]
    > Toutes les propriétés qui s’affichent sont grisées. Cela indique que ces propriétés sont propres à `lblDisplay` et ne peuvent pas être modifiées ou sélectionnées dans la fenêtre Propriétés. Par défaut, les contrôles contenus dans un contrôle composite sont à l’état `private`, et leurs propriétés ne sont accessibles d’aucune façon.

    > [!NOTE]
    > Si vous souhaitez que d’autres utilisateurs de votre contrôle composite puissent accéder à ses contrôles internes, définissez leur état sur `public` ou `protected`. Cela vous permettra de définir et de modifier les propriétés des contrôles contenus dans votre contrôle composite à l’aide du code approprié.

3. Ajoutez <xref:System.Windows.Forms.Label> un contrôle à votre commande composite.

4. À l’aide <xref:System.Windows.Forms.Label> de la souris, faites glisser le contrôle immédiatement sous la boîte d’affichage. Dans la fenêtre Propriétés, définissez les propriétés suivantes.

    |Propriété|Paramètre|
    |--------------|-------------|
    |**Nom   **|`lblAlarm`|
    |**Texte**|**Alarme!**|
    |**TextAlign**|`MiddleCenter`|
    |**Visible**|`false`|

### <a name="add-the-alarm-functionality"></a>Ajouter la fonctionnalité d’alarme

Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle permettant d’activer la fonctionnalité d’alarme dans votre contrôle composite. Dans cette procédure, vous allez ajouter du code pour comparer l’heure actuelle à l’heure de l’alarme et, si elles sont identiques, déclencher le clignotement de l’alarme. En remplaçant la méthode `timer1_Tick` de `ctlClock` et en lui ajoutant du code, vous allez étendre les capacités de `ctlAlarmClock` tout en conservant les fonctionnalités inhérentes de `ctlClock`.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Pour remplacer la méthode timer1_Tick de ctlClock

1. Dans **l’éditeur de code**, recherchez l’instruction `private bool blnAlarmSet;`. Juste en dessous de l’instruction, ajoutez l’instruction suivante.

    ```csharp
    private bool blnColorTicker;
    ```

2. Dans **l’éditeur de code**, recherchez l’accolade fermante (`})` à la fin de la classe. Juste avant l’accolade, ajoutez le code suivant.

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     L’ajout de ce code permet d’effectuer plusieurs tâches. L’instruction `override` ordonne au contrôle d’utiliser cette méthode à la place de la méthode héritée du contrôle de base. Lorsque cette méthode est appelée, elle appelle la méthode qu’elle remplace en appelant l’instruction `base.timer1_Tick`, ce qui permet de s’assurer que toutes les fonctionnalités intégrées au contrôle d’origine sont également intégrées à ce contrôle. Du code supplémentaire est ensuite exécuté pour intégrer la fonctionnalité d’alarme. Lorsque l’alarme se déclenche, un contrôle Étiquette clignotant apparaît.

     Votre contrôle d’alarme est presque terminé. La seule chose qui reste à faire est de mettre en place un moyen de le désactiver. Pour ce faire, vous allez ajouter du code à la méthode `lblAlarm_Click`.

#### <a name="to-implement-the-shutoff-method"></a>Pour implémenter la méthode de désactivation

1. Dans **Solution Explorer**, clic droit **ctlAlarmClock.cs**, puis cliquez sur View **Designer**.

     Le concepteur s’ouvre.

2. Ajoutez un bouton au contrôle. Définissez les propriétés du bouton comme suit.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom   **|`btnAlarmOff`|
    |**Texte**|**Désactiver l’alarme**|

3. Dans le concepteur, double-cliquez sur **btnAlarmOff**.

     **L’éditeur de code** s’ouvre à la ligne `private void btnAlarmOff_Click`.

4. Modifiez cette méthode afin qu’elle ressemble au code suivant.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.

### <a name="use-the-inherited-control-on-a-form"></a>Utilisez le contrôle hérité sur un formulaire

Vous pouvez tester votre contrôle hérité de la `ctlClock`même manière que vous avez testé le contrôle de la classe de base , : Appuyez sur **F5** pour construire le projet et exécuter votre contrôle dans le **conteneur d’essai UserControl**. Pour plus d’informations, consultez [Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Pour pouvoir utiliser votre contrôle, vous devrez l’héberger dans un formulaire. À l’instar d’un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de manière autonome et doit être hébergé dans un formulaire ou un autre conteneur. Étant donné que `ctlAlarmClock` présente davantage de fonctionnalités, du code supplémentaire est nécessaire pour le tester. Dans cette procédure, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`. Vous allez écrire du code pour définir et afficher la propriété `AlarmTime` de `ctlAlarmClock`, puis vous testerez ses fonctions inhérentes.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Pour générer votre contrôle et l’ajouter à un formulaire de test

1. Dans **Solution Explorer**, clic droit **ctlClockLib**, puis cliquez sur **Build**.

2. Ajoutez un nouveau projet **d’application de formulaires Windows** à la solution, et nommez-le **Test**.

3. Dans **Solution Explorer**, cliquez à droite sur le nœud **Références** pour votre projet de test. Cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**. Cliquez sur l’onglet intitulé **Projets**. Votre projet `ctlClockLib` s’affiche sous **Nom du projet**. Double-cliquez sur le projet pour ajouter la référence au projet de test.

4. Dans **Solution Explorer**, **test**à clic droit , puis cliquez sur **Build**.

5. Dans la **boîte à outils**, développez le nœud **Composants ctlClockLib**.

6. Double-cliquez sur **ctlAlarmClock** pour ajouter une copie de `ctlAlarmClock` à votre formulaire.

7. Dans la **boîte à outils**, localiser et double-cliquer **DateTimePicker** pour ajouter un <xref:System.Windows.Forms.DateTimePicker> contrôle à votre formulaire, puis ajouter un <xref:System.Windows.Forms.Label> contrôle en double-clic **Label**.

8. Utilisez la souris pour positionner les contrôles à un endroit approprié sur le formulaire.

9. Définissez les propriétés de ces contrôles de la manière suivante.

    |Control|Propriété|Valeur|
    |-------------|--------------|-----------|
    |`label1`|**Texte**|`(blank space)`|
    ||**Nom   **|`lblTest`|
    |`dateTimePicker1`|**Nom   **|`dtpTest`|
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. Dans le concepteur, double-cliquez sur **dtpTest**.

     **L’éditeur de code** s’ouvre à la ligne `private void dtpTest_ValueChanged`.

11. Modifiez le code afin qu’il ressemble à l’exemple de code suivant.

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. Dans **Solution Explorer**, **test**à clic droit , puis cliquez sur Set **as StartUp Project**.

13. Sur le menu **Debug,** cliquez sur **Démarrer Debugging**.

     Le programme de test démarre. Notez que l’heure `ctlAlarmClock` actuelle est mise à jour dans <xref:System.Windows.Forms.DateTimePicker> le contrôle, et que l’heure de départ est indiquée dans le contrôle.

14. Cliquez <xref:System.Windows.Forms.DateTimePicker> sur l’endroit où les minutes de l’heure sont affichées.

15. À l’aide du clavier, définissez une valeur pour les minutes comportant une minute de plus que l’heure actuelle affichée par `ctlAlarmClock`.

     L’heure de déclenchement de l’alarme apparaît dans `lblTest`. Attendez que l’heure affichée atteigne l’heure de déclenchement de l’alarme. Lorsque l’heure affichée atteint l’heure sur laquelle l’alarme a été définie, `lblAlarm` se met à clignoter.

16. Désactivez l’alarme en cliquant sur `btnAlarmOff`. Vous pouvez maintenant réinitialiser l’alarme.

Cet article a couvert un certain nombre de concepts clés. Vous avez appris à créer un contrôle composite en combinant des contrôles et des composants dans un conteneur de contrôle composite. Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code pour implémenter des fonctionnalités personnalisées. Dans la dernière section, vous avez appris à étendre les fonctionnalités d’un contrôle composite grâce à l’héritage et à modifier les fonctionnalités des méthodes hôtes en remplaçant ces méthodes.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Procédure pas à pas : héritage d'un contrôle Windows Forms à l'aide de Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
