---
title: 'Procédure pas à pas : création d’une application Windows accessible'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: de25c3dcf33471a1aadb4445a83affab9c40914b
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306340"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Procédure pas à pas : création d’une application Windows accessible

La création d'une application accessible implique de nombreuses contraintes pour l'entreprise. De nombreux gouvernements ont mis en place une réglementation relative à l'accessibilité pour l'achat des logiciels. Le logo Certifié pour Windows inclut des normes d’accessibilité. Rien qu’aux États-Unis, on estime à 30 millions le nombre de personnes affectées par l’accessibilité des logiciels, dont beaucoup sont des clients potentiels.

Cette procédure pas à pas traite des cinq critères d’accessibilité pour le logo Certifié pour Windows. Selon ces critères, une application accessible doit :

- prendre en charge les paramètres de taille, de couleurs, de police et d'entrée du Panneau de configuration ; La barre de menus, la barre de titre, les bordures et la barre d'état sont redimensionnés automatiquement quand l'utilisateur modifie les paramètres du Panneau de configuration. Aucune autre modification des contrôles ou du code n'est nécessaire dans cette application.

- prendre en charge le mode de contraste élevé ;

- fournir un accès au clavier documenté à toutes les fonctionnalités ;

- exposer l'emplacement du focus clavier visuellement et par programmation ;

- éviter de transmettre des informations importantes uniquement par voie sonore.

Pour plus d’informations, consultez [Ressources pour la conception d’applications accessibles](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Pour plus d’informations sur la prise en charge des différentes dispositions du clavier, consultez [Bonnes pratiques pour développer des applications mondialisables](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Création du projet

Cette procédure pas à pas crée l'interface utilisateur pour une application de commande de pizza. Elle se compose d'un <xref:System.Windows.Forms.TextBox> pour le nom du client, d'un groupe <xref:System.Windows.Forms.RadioButton> pour sélectionner la taille de la pizza, d'un <xref:System.Windows.Forms.CheckedListBox> pour sélectionner les ingrédients, de deux contrôles bouton étiquetés Commande et Annuler et d'un menu avec une commande Quitter.

L'utilisateur entre le nom du client, la taille de la pizza et les ingrédients souhaités. Quand l'utilisateur clique sur le bouton de commande, un résumé de la commande et son prix sont affichés dans une boîte de message et les contrôles sont effacés et prêts pour la commande suivante. Quand l'utilisateur clique sur le bouton Annuler, les contrôles sont effacés et prêts pour la commande suivante. Quand l'utilisateur clique sur l'élément de menu Quitter, le programme se ferme.

L'objectif principal de cette procédure pas à pas n'est pas d'illustrer le code pour un système de commande de vente au détail, mais l'accessibilité de l'interface utilisateur. La procédure pas à pas illustre les fonctionnalités d'accessibilité de plusieurs contrôles courants, y compris les boutons, les cases d'option, les zones de texte et les étiquettes.

#### <a name="to-begin-making-the-application"></a>Pour commencer à créer l'application

- Créez une nouvelle application Windows dans Visual Basic ou Visual C#. Nommez le projet **PizzaOrder**. (Pour plus d’informations, consultez [Création de projets et de solutions](/visualstudio/ide/creating-solutions-and-projects).)

## <a name="adding-the-controls-to-the-form"></a>Ajout des contrôles au formulaire

Lors de l'ajout des contrôles à un formulaire, veillez à respecter les consignes d'accessibilité suivantes :

- Définissez les propriétés <xref:System.Windows.Forms.Control.AccessibleDescription%2A> et <xref:System.Windows.Forms.Control.AccessibleName%2A>. Dans cet exemple, le paramètre Default pour <xref:System.Windows.Forms.Control.AccessibleRole%2A> est suffisant. Pour plus d’informations sur les propriétés d’accessibilité, consultez [Informations d’accessibilité sur les contrôles d’un Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Définissez la taille de police sur 10 points ou plus.

  > [!NOTE]
  > Si vous affectez la valeur 10 à la taille de police du formulaire quand vous commencez, tous les contrôles qui seront ensuite ajoutés au formulaire auront une taille de police de 10.

- Assurez-vous que tous les contrôles Label qui décrivent un contrôle TextBox précèdent immédiatement le contrôle TextBox dans l'ordre de tabulation.

- Ajoutez une touche d’accès, en utilisant le caractère « & », <xref:System.Windows.Forms.Control.Text%2A> à la propriété de n’importe quel contrôle auquel l’utilisateur peut accéder.

- Ajoutez une touche d’accès, en utilisant le caractère « & », <xref:System.Windows.Forms.Control.Text%2A> à la propriété de l’étiquette qui précède un contrôle auquel l’utilisateur peut accéder. Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> des étiquettes pour que le focus soit défini sur le contrôle suivant dans l'ordre de tabulation quand l'utilisateur appuie sur la touche d'accès.

- Ajoutez des touches d'accès rapide à tous les éléments de menu.

#### <a name="to-make-your-windows-application-accessible"></a>Pour rendre votre application Windows accessible

- Ajoutez les contrôles au formulaire et définissez les propriétés comme décrit ci-dessous. Pour obtenir un modèle décrivant comment organiser les contrôles sur le formulaire, consultez l'image à la fin du tableau.

   |Object|Propriété|Value|
   |------------|--------------|-----------|
   |Form1|AccessibleDescription|Formulaire de commande|
   ||AccessibleName|Formulaire de commande|
   ||Taille de police|10|
   ||Text|Formulaire de commande de pizza|
   |PictureBox|Name|logo|
   ||AccessibleDescription|Une tranche de pizza|
   ||AccessibleName|Logo de la société|
   ||Image|Une icône ou bitmap quelconque|
   |Etiquette|Name|companyLabel|
   ||Text|Bonne Pizza|
   ||TabIndex|1|
   ||AccessibleDescription|Nom de la société|
   ||AccessibleName|Nom de la société|
   ||BackColor|Bleu|
   ||ForeColor|Jaune|
   ||Taille de police|18|
   |Label|Name|customerLabel|
   ||Text|&Nom|
   ||TabIndex|2|
   ||AccessibleDescription|Étiquette du nom de client|
   ||AccessibleName|Étiquette du nom de client|
   ||UseMnemonic|True|
   |TextBox|Name|CustomerName|
   ||Text|(aucune)|
   ||TabIndex|3|
   ||AccessibleDescription|Nom du client|
   ||AccessibleName|Nom du client|
   |GroupBox|Name|sizeOptions|
   ||AccessibleDescription|Options de taille de pizza|
   ||AccessibleName|Options de taille de pizza|
   ||Text|Taille de la pizza|
   ||TabIndex|4|
   |RadioButton|Name|smallPizza|
   ||Text|&Petite €6,00|
   ||Activé|True|
   ||TabIndex|0|
   ||AccessibleDescription|Petite pizza|
   ||AccessibleName|Petite pizza|
   |RadioButton|Name|largePizza|
   ||Text|&Grande €10,00|
   ||TabIndex|1|
   ||AccessibleDescription|Grande pizza|
   ||AccessibleName|Grande pizza|
   |Etiquette|Name|toppingsLabel|
   ||Text|&Garniture (€0,75 chacune)|
   ||TabIndex|5|
   ||AccessibleDescription|Étiquette de garniture|
   ||AccessibleName|Étiquette de garniture|
   ||UseMnemonic|True|
   |CheckedListBox|Name|Garniture|
   ||TabIndex|6\.|
   ||AccessibleDescription|Garniture disponible|
   ||AccessibleName|Garniture disponible|
   ||Éléments|Pepperoni, Saucisson, Champignons|
   |Button|Name|order|
   ||Text|&Commande|
   ||TabIndex|7|
   ||AccessibleDescription|Total de la commande|
   ||AccessibleName|Total de la commande|
   |Bouton|Name|cancel|
   ||Text|Annu&ler|
   ||TabIndex|8|
   ||AccessibleDescription|Annuler la commande|
   ||AccessibleName|Annuler la commande|
   |MainMenu|Name|theMainMenu|
   |MenuItem|Name|fileCommands|
   ||Text|&Fichier|
   |MenuItem|Name|exitApp|
   ||Text|&Quitter|

   Votre formulaire doit ressembler à l’image suivante :

   ![Le formulaire de commande de pizza avec une zone de texte nom, et la sélection de la taille et des pings.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Prise en charge du mode de contraste élevé

Le mode de contraste élevé est un paramètre système Windows qui améliore la lisibilité en utilisant des couleurs contrastées et des tailles de polices adaptées aux personnes malvoyantes. La <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> propriété est fournie pour déterminer si le mode de contraste élevé est défini.

Si SystemInformation.HighContrast a la valeur `true`, l'application doit :

- afficher tous les éléments d'interface utilisateur à l'aide du modèle de couleurs système ;

- transmettre via des signaux visuels ou sonores toute information qui est transmise via une couleur. Par exemple, si certains éléments de liste sont mis en surbrillance à l'aide d'une police rouge, vous pourriez également ajouter la mise en gras pour que l'utilisateur ait un autre indicateur que la couleur ;

- omettre toutes les images ou tous les motifs derrière le texte.

L'application doit vérifier le paramètre de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> quand elle démarre et répond à l'événement système <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. L'événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> est déclenché chaque fois que la valeur de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> change.

Dans notre application, le seul élément qui n’utilise pas les paramètres système pour la couleur est `lblCompanyName`. La <xref:System.Drawing.SystemColors> classe est utilisée pour modifier les paramètres de couleur de l’étiquette sur les couleurs système sélectionnées par l’utilisateur.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Pour activer le mode de contraste élevé de manière efficace

1. Créez une méthode pour affecter les couleurs système comme couleurs de l'étiquette.

    ```vb
    Private Sub SetColorScheme()
        If SystemInformation.HighContrast Then
            companyLabel.BackColor = SystemColors.Window
            companyLabel.ForeColor = SystemColors.WindowText
        Else
            companyLabel.BackColor = Color.Blue
            companyLabel.ForeColor = Color.Yellow
        End If
    End Sub
    ```

    ```csharp
    private void SetColorScheme()
    {
        if (SystemInformation.HighContrast)
        {
            companyLabel.BackColor = SystemColors.Window;
            companyLabel.ForeColor = SystemColors.WindowText;
        }
        else
        {
            companyLabel.BackColor = Color.Blue;
            companyLabel.ForeColor = Color.Yellow;
        }
    }
    ```

2. Appelez la procédure `SetColorScheme` dans le constructeur de formulaire (`Public Sub New()` en Visual Basic et `public Form1()` en Visual C#). Pour accéder au constructeur en Visual Basic, vous devez développer la région nommée **Code généré par le Concepteur Windows Form**.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. Créez une procédure événementielle, avec la signature appropriée, pour répondre à l'événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. Ajoutez du code au constructeur de formulaire, après l’appel à `InitializeComponents`, pour raccorder la procédure événementielle à l’événement système. Cette méthode appelle la procédure `SetColorScheme`.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. Ajoutez du code à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> du formulaire, avant l’appel à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> de la classe de base, pour libérer l’événement quand l’application se ferme. Pour accéder à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> en Visual Basic, vous devez développer la région étiquetée Code généré par le Concepteur Windows Form.

    > [!NOTE]
    > Le code d'événement système exécute un thread distinct de l'application principale. Si vous ne libérez pas l'événement, le code que vous raccordez à l'événement s'exécute même après la fermeture du programme.

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. Appuyez sur F5 pour exécuter l'application.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Communication d'informations importantes par un moyen autre que le son

Dans cette application, aucune information n'est communiquée que par du son. Si vous utilisez du son dans votre application, vous devez aussi fournir des informations par d'autres moyens.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Pour fournir des informations par d'autres moyens que le son

1. Faites clignoter la barre de titre à l'aide de la fonction d'API Windows FlashWindow. Pour obtenir un exemple d’appel de fonctions API Windows, consultez [procédure pas à pas : Appel des API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)Windows.

    > [!NOTE]
    > L'utilisateur a peut-être activé le service SoundSentry Windows, qui provoque aussi le clignotement de la fenêtre quand des sons système sont lus par le haut-parleur intégré de l'ordinateur.

2. Affichez les informations importantes dans une fenêtre non modale, pour que l'utilisateur puisse y répondre.

3. Affichez une boîte de message qui acquiert le focus clavier. Évitez cette méthode quand l'utilisateur est susceptible de taper du texte au clavier.

4. Affichez un indicateur d’état dans la zone de notification d’état de la barre des tâches. Pour plus d’informations, consultez [Ajout d’icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Test de l'application

Avant de déployer l'application, vous devez tester les fonctionnalités d'accessibilité que vous avez implémentées.

#### <a name="to-test-accessibility-features"></a>Pour tester les fonctionnalités d'accessibilité

1. Pour tester l'accès au clavier, débranchez la souris et parcourez l'interface utilisateur pour chaque fonctionnalité en utilisant uniquement le clavier. Assurez-vous que toutes les tâches peuvent être effectuées en utilisant seulement le clavier.

2. Pour tester la prise en charge du contraste élevé, choisissez l'icône Options d'accessibilité dans le Panneau de configuration. Cliquez sur l'onglet Affichage et cochez la case Utiliser le contraste élevé. Parcourez tous les éléments d'interface utilisateur pour vous assurer que les modifications de couleur et de police sont répercutées. Assurez-vous également que les images et les motifs placés derrière le texte sont omis.

    > [!NOTE]
    > Le Panneau de configuration de Windows NT 4 ne contient pas d'icône Options d'accessibilité. Ainsi, cette procédure de modification du paramètre SystemInformation.HighContrast ne fonctionne pas dans Windows NT 4.

3. D'autres outils sont disponibles pour tester l'accessibilité d'une application.

4. Pour tester l'exposition du focus clavier, exécutez la Loupe. (Pour l’ouvrir, cliquez sur le menu **Démarrer**, pointez sur **Programmes**, sur **Accessoires**, sur **Accessibilité**, puis cliquez sur **Loupe**.) Parcourez l'interface utilisateur à l'aide de la tabulation de clavier et de la souris. Vérifiez que tous les déplacements sont correctement suivis dans la **Loupe**.

5. Pour tester l'exposition des éléments à l'écran, exécutez Inspect et utilisez la souris et la touche de tabulation pour atteindre chaque élément. Assurez-vous que les informations présentées dans les champs Name, State, Role, Location et Value de la fenêtre Inspect sont significatives pour l'utilisateur pour chaque objet de l'interface utilisateur.
