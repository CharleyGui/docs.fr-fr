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
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="76e14-102">Procédure : valider les paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="76e14-102">How to: Validate Application Settings</span></span>

<span data-ttu-id="76e14-103">Cette rubrique illustre la validation des paramètres d’application avant qu’ils ne soient rendus persistants.</span><span class="sxs-lookup"><span data-stu-id="76e14-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>

<span data-ttu-id="76e14-104">Les paramètres d’application fortement typés empêchent les utilisateurs d’affecter les données d’un type incorrect pour un paramètre donné.</span><span class="sxs-lookup"><span data-stu-id="76e14-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="76e14-105">Toutefois, un utilisateur peut essayer d’assigner une valeur à un paramètre qui se situe en dehors des limites acceptables, par exemple en fournissant une date de naissance future.</span><span class="sxs-lookup"><span data-stu-id="76e14-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="76e14-106"><xref:System.Configuration.ApplicationSettingsBase>, la classe parente de toutes les classes de paramètres d’application, expose quatre événements pour permettre la vérification de ces limites.</span><span class="sxs-lookup"><span data-stu-id="76e14-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="76e14-107">La gestion de ces événements place la totalité de votre code de validation dans un emplacement unique, plutôt que de le répartir dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="76e14-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>

<span data-ttu-id="76e14-108">L’événement que vous utilisez dépend du moment où vous devez valider vos paramètres, comme décrit dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="76e14-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>

|<span data-ttu-id="76e14-109">Événement</span><span class="sxs-lookup"><span data-stu-id="76e14-109">Event</span></span>|<span data-ttu-id="76e14-110">Occurrence et utilisation</span><span class="sxs-lookup"><span data-stu-id="76e14-110">Occurrence and use</span></span>|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="76e14-111">Se produit après le chargement initial d’un groupe de propriétés de paramètres.</span><span class="sxs-lookup"><span data-stu-id="76e14-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="76e14-112">Utilisez cet événement pour valider les valeurs initiales de l’ensemble du groupe de propriétés avant de les utiliser dans l’application.</span><span class="sxs-lookup"><span data-stu-id="76e14-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="76e14-113">Se produit avant la modification de la valeur d’une propriété unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="76e14-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="76e14-114">Utilisez cet événement pour valider une propriété unique avant sa modification.</span><span class="sxs-lookup"><span data-stu-id="76e14-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="76e14-115">Il peut fournir des commentaires immédiats aux utilisateurs à propos de leurs actions et de leurs choix.</span><span class="sxs-lookup"><span data-stu-id="76e14-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="76e14-116">Se produit après la modification de la valeur d’une propriété unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="76e14-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="76e14-117">Utilisez cet événement pour valider une propriété unique après sa modification.</span><span class="sxs-lookup"><span data-stu-id="76e14-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="76e14-118">Cet événement est rarement utilisé pour la validation, sauf si un processus de validation long et asynchrone est requis.</span><span class="sxs-lookup"><span data-stu-id="76e14-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="76e14-119">Se produit avant que le groupe de propriétés de paramètres ne soit stocké.</span><span class="sxs-lookup"><span data-stu-id="76e14-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="76e14-120">Utilisez cet événement pour valider les valeurs de l’ensemble du groupe de propriétés avant qu’elles ne soient rendues persistantes sur le disque.</span><span class="sxs-lookup"><span data-stu-id="76e14-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|

<span data-ttu-id="76e14-121">En règle générale, vous n’utiliserez pas tous ces événements dans la même application à des fins de validation.</span><span class="sxs-lookup"><span data-stu-id="76e14-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="76e14-122">Par exemple, il est souvent possible de répondre à toutes les exigences de validation en <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> gérant uniquement l’événement.</span><span class="sxs-lookup"><span data-stu-id="76e14-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

<span data-ttu-id="76e14-123">Un gestionnaire d’événements exécute généralement l’une des actions suivantes lorsqu’il détecte une valeur non valide :</span><span class="sxs-lookup"><span data-stu-id="76e14-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>

- <span data-ttu-id="76e14-124">Fournit automatiquement une valeur correcte, par exemple la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="76e14-124">Automatically supplies a value known to be correct, such as the default value.</span></span>

- <span data-ttu-id="76e14-125">Interroge de nouveau l’utilisateur de code serveur pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="76e14-125">Re-queries the user of server code for information.</span></span>

- <span data-ttu-id="76e14-126">Pour les événements déclenchés avant leurs actions associées, <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> tels <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>que et, <xref:System.ComponentModel.CancelEventArgs> utilise l’argument pour annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="76e14-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>

<span data-ttu-id="76e14-127">Pour plus d’informations sur la gestion des événements, consultez [Vue d’ensemble des gestionnaires d’événements](../event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="76e14-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>

<span data-ttu-id="76e14-128">Les procédures suivantes montrent comment tester une date de naissance valide à l’aide de <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> l' <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> événement ou.</span><span class="sxs-lookup"><span data-stu-id="76e14-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="76e14-129">Ces procédures ont été écrites en supposant que vous avez déjà créé vos paramètres d’application. Dans cet exemple, nous vérifions les limites d’un paramètre nommé `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="76e14-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="76e14-130">Pour plus d’informations sur la création de [paramètres, consultez Procédure: Créer des paramètres](how-to-create-application-settings.md)d’application.</span><span class="sxs-lookup"><span data-stu-id="76e14-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>

### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="76e14-131">Pour obtenir l’objet des paramètres de l’application</span><span class="sxs-lookup"><span data-stu-id="76e14-131">To obtain the application settings object</span></span>

- <span data-ttu-id="76e14-132">Obtenez une référence à l’objet des paramètres d’application (instance de wrapper) en respectant l’un des éléments de la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="76e14-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>

  - <span data-ttu-id="76e14-133">Si vous avez créé vos paramètres à l’aide de la boîte de dialogue Paramètres de l’application Visual Studio de l’**éditeur de propriétés**, vous pouvez récupérer l’objet de paramètres par défaut généré pour votre langage par le biais de l’expression suivante.</span><span class="sxs-lookup"><span data-stu-id="76e14-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    <span data-ttu-id="76e14-134">ou</span><span class="sxs-lookup"><span data-stu-id="76e14-134">-or-</span></span>

  - <span data-ttu-id="76e14-135">Si vous êtes un développeur Visual Basic et si vous avez créé vos paramètres d’application à l’aide du Concepteur de projet, vous pouvez récupérer vos paramètres à l’aide de l’[objet My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="76e14-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>

    <span data-ttu-id="76e14-136">ou</span><span class="sxs-lookup"><span data-stu-id="76e14-136">-or-</span></span>

  - <span data-ttu-id="76e14-137">Si vous avez créé vos paramètres en dérivant directement <xref:System.Configuration.ApplicationSettingsBase> de, vous devez instancier votre classe manuellement.</span><span class="sxs-lookup"><span data-stu-id="76e14-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

<span data-ttu-id="76e14-138">Les procédures suivantes ont été écrites en supposant que l’objet des paramètres d’application a été obtenu par le biais du dernier élément répertorié dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="76e14-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="76e14-139">Pour valider les paramètres de l’application lors de la modification d’un paramètre</span><span class="sxs-lookup"><span data-stu-id="76e14-139">To validate Application Settings when a setting is changing</span></span>

1. <span data-ttu-id="76e14-140">Si vous êtes un C# développeur, dans l’événement de `Load` votre formulaire ou contrôle, ajoutez un gestionnaire d’événements pour l' <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> événement.</span><span class="sxs-lookup"><span data-stu-id="76e14-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

    <span data-ttu-id="76e14-141">ou</span><span class="sxs-lookup"><span data-stu-id="76e14-141">-or-</span></span>

    <span data-ttu-id="76e14-142">Si vous êtes un développeur Visual Basic, vous devez déclarer la variable `Settings` à l’aide du mot clé`WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="76e14-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>

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

2. <span data-ttu-id="76e14-143">Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.</span><span class="sxs-lookup"><span data-stu-id="76e14-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

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

### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="76e14-144">Pour valider les paramètres d’application en cas d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="76e14-144">To validate Application Settings when a Save occurs</span></span>

1. <span data-ttu-id="76e14-145">Dans l' `Load` événement de votre formulaire ou contrôle, ajoutez un gestionnaire d’événements <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="76e14-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>

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

2. <span data-ttu-id="76e14-146">Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.</span><span class="sxs-lookup"><span data-stu-id="76e14-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="76e14-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76e14-147">See also</span></span>

- [<span data-ttu-id="76e14-148">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76e14-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="76e14-149">Guide pratique : Créer des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="76e14-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
