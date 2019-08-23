---
title: 'Procédure : valider les paramètres d’application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: 220b86c0de57e60036527bb49f2d8de46390a9ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929788"
---
# <a name="how-to-validate-application-settings"></a>Procédure : valider les paramètres d’application

Cette rubrique illustre la validation des paramètres d’application avant qu’ils ne soient rendus persistants.

Les paramètres d’application fortement typés empêchent les utilisateurs d’affecter les données d’un type incorrect pour un paramètre donné. Toutefois, un utilisateur peut essayer d’assigner une valeur à un paramètre qui se situe en dehors des limites acceptables, par exemple en fournissant une date de naissance future. <xref:System.Configuration.ApplicationSettingsBase>, la classe parente de toutes les classes de paramètres d’application, expose quatre événements pour permettre la vérification de ces limites. La gestion de ces événements place la totalité de votre code de validation dans un emplacement unique, plutôt que de le répartir dans votre projet.

L’événement que vous utilisez dépend du moment où vous devez valider vos paramètres, comme décrit dans le tableau suivant.

|Événement|Occurrence et utilisation|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Se produit après le chargement initial d’un groupe de propriétés de paramètres.<br /><br /> Utilisez cet événement pour valider les valeurs initiales de l’ensemble du groupe de propriétés avant de les utiliser dans l’application.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Se produit avant la modification de la valeur d’une propriété unique de paramètres.<br /><br /> Utilisez cet événement pour valider une propriété unique avant sa modification. Il peut fournir des commentaires immédiats aux utilisateurs à propos de leurs actions et de leurs choix.|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Se produit après la modification de la valeur d’une propriété unique de paramètres.<br /><br /> Utilisez cet événement pour valider une propriété unique après sa modification. Cet événement est rarement utilisé pour la validation, sauf si un processus de validation long et asynchrone est requis.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Se produit avant que le groupe de propriétés de paramètres ne soit stocké.<br /><br /> Utilisez cet événement pour valider les valeurs de l’ensemble du groupe de propriétés avant qu’elles ne soient rendues persistantes sur le disque.|

En règle générale, vous n’utiliserez pas tous ces événements dans la même application à des fins de validation. Par exemple, il est souvent possible de répondre à toutes les exigences de validation en <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> gérant uniquement l’événement.

Un gestionnaire d’événements exécute généralement l’une des actions suivantes lorsqu’il détecte une valeur non valide :

- Fournit automatiquement une valeur correcte, par exemple la valeur par défaut.

- Interroge de nouveau l’utilisateur de code serveur pour plus d’informations.

- Pour les événements déclenchés avant leurs actions associées, <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> tels <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>que et, <xref:System.ComponentModel.CancelEventArgs> utilise l’argument pour annuler l’opération.

Pour plus d’informations sur la gestion des événements, consultez [Vue d’ensemble des gestionnaires d’événements](../event-handlers-overview-windows-forms.md).

Les procédures suivantes montrent comment tester une date de naissance valide à l’aide de <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> l' <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> événement ou. Ces procédures ont été écrites en supposant que vous avez déjà créé vos paramètres d’application. Dans cet exemple, nous vérifions les limites d’un paramètre nommé `DateOfBirth`. Pour plus d’informations sur la création de [paramètres, consultez Procédure: Créer des paramètres](how-to-create-application-settings.md)d’application.

### <a name="to-obtain-the-application-settings-object"></a>Pour obtenir l’objet des paramètres de l’application

- Obtenez une référence à l’objet des paramètres d’application (instance de wrapper) en respectant l’un des éléments de la liste suivante :

  - Si vous avez créé vos paramètres à l’aide de la boîte de dialogue Paramètres de l’application Visual Studio de l’**éditeur de propriétés**, vous pouvez récupérer l’objet de paramètres par défaut généré pour votre langage par le biais de l’expression suivante.

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    ou

  - Si vous êtes un développeur Visual Basic et si vous avez créé vos paramètres d’application à l’aide du Concepteur de projet, vous pouvez récupérer vos paramètres à l’aide de l’[objet My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).

    ou

  - Si vous avez créé vos paramètres en dérivant directement <xref:System.Configuration.ApplicationSettingsBase> de, vous devez instancier votre classe manuellement.

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

Les procédures suivantes ont été écrites en supposant que l’objet des paramètres d’application a été obtenu par le biais du dernier élément répertorié dans cette procédure.

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Pour valider les paramètres de l’application lors de la modification d’un paramètre

1. Si vous êtes un C# développeur, dans l’événement de `Load` votre formulaire ou contrôle, ajoutez un gestionnaire d’événements pour l' <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> événement.

    ou

    Si vous êtes un développeur Visual Basic, vous devez déclarer la variable `Settings` à l’aide du mot clé`WithEvents`.

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);
    }
    ```

    ```vb
    Public Sub Form1_Load(sender as Object, e as EventArgs)
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging
    End Sub
    ```

2. Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.

    ```csharp
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)
    {
        if (e.SettingName.Equals("DateOfBirth")) {
            Date newDate = (Date)e.NewValue;
            If (newDate > Date.Now) {
                e.Cancel = true;
                // Inform the user.
            }
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging
        If (e.SettingName.Equals("DateOfBirth")) Then
            Dim NewDate as Date = CType(e.NewValue, Date)
            If (NewDate > Date.Now) Then
                e.Cancel = True
                ' Inform the user.
            End If
        End If
    End Sub
    ```

### <a name="to-validate-application-settings-when-a-save-occurs"></a>Pour valider les paramètres d’application en cas d’enregistrement

1. Dans l' `Load` événement de votre formulaire ou contrôle, ajoutez un gestionnaire d’événements <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> pour l’événement.

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);
    }
    ```

    ```vb
    Public Sub Form1_Load(Sender as Object, e as EventArgs)
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving
    End Sub
    ```

2. Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.

    ```csharp
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)
    {
        if (this["DateOfBirth"] > Date.Now) {
            e.Cancel = true;
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)
        If (Me["DateOfBirth"] > Date.Now) Then
            e.Cancel = True
        End If
    End Sub
    ```

## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans les Windows Forms](../creating-event-handlers-in-windows-forms.md)
- [Guide pratique : Créer des paramètres d’application](how-to-create-application-settings.md)
