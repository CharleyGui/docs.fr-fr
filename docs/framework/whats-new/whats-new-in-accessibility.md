---
title: Nouveautés du .NET Framework dans le domaine de l’accessibilité
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 6f17cb0fb6e5b0457af745ea0d089f3e51d4706c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938146"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="01d82-102">Nouveautés du .NET Framework dans le domaine de l’accessibilité</span><span class="sxs-lookup"><span data-stu-id="01d82-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="01d82-103">Le .NET Framework vise à rendre les applications plus accessibles pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="01d82-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="01d82-104">Les fonctionnalités d’accessibilité permettent à une application de fournir une expérience appropriée pour les utilisateurs des technologies d’assistance.</span><span class="sxs-lookup"><span data-stu-id="01d82-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="01d82-105">La version 4.7.1 de .NET Framework inclut de nombreuses améliorations au niveau de l’accessibilité, qui permettent aux développeurs de créer des applications accessibles.</span><span class="sxs-lookup"><span data-stu-id="01d82-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="01d82-106">Commutateurs d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="01d82-106">Accessibility switches</span></span>

<span data-ttu-id="01d82-107">Si votre application cible .NET Framework 4.7 ou une version antérieure, mais est exécutée sur .NET Framework 4.7.1 ou une version ultérieure, vous pouvez la configurer pour qu’elle active les fonctionnalités d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="01d82-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="01d82-108">Si elle cible .NET Framework 4.7.1 ou une version ultérieure, vous pouvez également la configurer afin qu’elle utilise les fonctionnalités héritées (et ainsi, qu’elle n’active pas les fonctionnalités d’accessibilité).</span><span class="sxs-lookup"><span data-stu-id="01d82-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="01d82-109">Chaque version du .NET Framework qui inclut des fonctionnalités d’accessibilité a son propre commutateur d’accessibilité, que vous ajoutez à l’élément [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](../configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="01d82-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="01d82-110">Les commutateurs pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-110">The following are the supported switches:</span></span>

|<span data-ttu-id="01d82-111">Version</span><span class="sxs-lookup"><span data-stu-id="01d82-111">Version</span></span>|<span data-ttu-id="01d82-112">Basculer</span><span class="sxs-lookup"><span data-stu-id="01d82-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="01d82-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="01d82-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="01d82-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="01d82-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="01d82-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="01d82-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="01d82-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="01d82-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="01d82-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="01d82-117">.NET Framework 4.8</span></span>|<span data-ttu-id="01d82-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="01d82-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="01d82-119">Activation des nouvelles fonctionnalités d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="01d82-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="01d82-120">Les nouvelles fonctionnalités d’accessibilité sont activées par défaut pour les applications qui ciblent .NET Framework 4.7.1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="01d82-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="01d82-121">De plus, pour les applications qui ciblent une version antérieure de .NET Framework mais qui sont exécutées sur .NET Framework 4.7.1 ou une version ultérieure, vous pouvez désactiver les comportements d’accessibilité hérités (et ainsi, utiliser les nouvelles fonctionnalités d’accessibilité) en ajoutant des commutateurs à l’élément [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](../configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application et en les définissant sur la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="01d82-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="01d82-122">Le code ci-dessous montre comment activer les nouvelles fonctionnalités d’accessibilité de .NET Framework 4.7.1 :</span><span class="sxs-lookup"><span data-stu-id="01d82-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="01d82-123">Si vous choisissez d’activer les fonctionnalités d’accessibilité d’une version ultérieure du .NET Framework, vous devez aussi activer explicitement les fonctionnalités des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="01d82-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="01d82-124">Pour configurer votre application afin qu’elle utilise les nouvelles fonctionnalités d’accessibilité des deux versions de .NET Framework (4.7.1 et 4.7.2), vous devez ajouter l’élément [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant :</span><span class="sxs-lookup"><span data-stu-id="01d82-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="01d82-125">Pour configurer votre application afin qu’elle utilise les nouvelles fonctionnalités d’accessibilité des versions 4.7.1, 4.7.2 et 4.8 de .NET Framework, vous devez ajouter l’élément [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant :</span><span class="sxs-lookup"><span data-stu-id="01d82-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="01d82-126">Restauration du comportement hérité</span><span class="sxs-lookup"><span data-stu-id="01d82-126">Restoring legacy behavior</span></span>

<span data-ttu-id="01d82-127">Pour les applications ciblant la version 4.7.1 ou des versions ultérieures du .NET Framework, vous pouvez désactiver les fonctionnalités d’accessibilité en ajoutant des commutateurs à l’élément [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](../configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application et en les définissant à la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="01d82-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="01d82-128">Par exemple, la configuration suivante active les nouvelles fonctionnalités d’accessibilité de .NET Framework 4.7.2 :</span><span class="sxs-lookup"><span data-stu-id="01d82-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="01d82-129">Nouveautés concernant l’accessibilité dans .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="01d82-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="01d82-130">.NET Framework 4.8 apporte de nouvelles fonctionnalités d’accessibilité dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="01d82-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="01d82-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="01d82-133">Concepteur de flux de travail Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="01d82-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="01d82-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-134">Windows Forms</span></span>

<span data-ttu-id="01d82-135">Dans .NET Framework 4.8, Windows Forms prend en charge les zones dynamiques et les événements de notification pour de nombreux contrôles couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="01d82-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="01d82-136">Il prend également en charge les info-bulles lorsqu’un utilisateur accède à un contrôle à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="01d82-137">**Prise en charge des zones dynamiques UIA dans les étiquettes et les StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="01d82-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="01d82-138">Les zones dynamiques UIA permettent aux développeurs d’applications d’informer les lecteurs d’écran lorsqu’une modification a été apportée au texte d’un contrôle qui se trouve dans un emplacement autre que celui où l’utilisateur travaille actuellement.</span><span class="sxs-lookup"><span data-stu-id="01d82-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="01d82-139">Cela s’avère utile, par exemple, lorsqu’un contrôle <xref:System.Windows.Forms.StatusStrip> affiche l’état d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="01d82-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="01d82-140">Si la connexion est supprimée et l’état change, le développeur peut souhaiter en informer le lecteur d’écran.</span><span class="sxs-lookup"><span data-stu-id="01d82-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="01d82-141">À compter de .NET Framework 4.8, Windows Forms implémente les zones dynamiques UIA pour les contrôles <xref:System.Windows.Forms.Label> et <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="01d82-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="01d82-142">Par exemple, le code suivant utilise la zone dynamique dans un contrôle <xref:System.Windows.Forms.Label> nommé `label1` :</span><span class="sxs-lookup"><span data-stu-id="01d82-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="01d82-143">Le narrateur annonce « Prêt », quel que soit l’endroit où l’utilisateur interagit avec l’application.</span><span class="sxs-lookup"><span data-stu-id="01d82-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="01d82-144">Vous pouvez également implémenter votre <xref:System.Windows.Forms.UserControl> comme une zone dynamique :</span><span class="sxs-lookup"><span data-stu-id="01d82-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="01d82-145">**Événements de notification UIA**</span><span class="sxs-lookup"><span data-stu-id="01d82-145">**UIA notification events**</span></span>

<span data-ttu-id="01d82-146">L’événement de notification UIA, qui a fait sa première apparition dans Windows 10 Fall Creators Update, permet à votre application de déclencher un événement UIA. Ainsi, le narrateur émet simplement une annonce en fonction du texte que vous fournissez avec l’événement, sans avoir besoin d’un contrôle correspondant dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="01d82-147">Dans certains scénarios, il s’agit d’une méthode simple pour améliorer considérablement l’accessibilité de votre application.</span><span class="sxs-lookup"><span data-stu-id="01d82-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="01d82-148">Elle peut également être utile pour informer de la progression d’un processus qui peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="01d82-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="01d82-149">Pour plus d’informations sur les événements de notification UIA, consultez [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="01d82-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="01d82-150">L’exemple suivant déclenche l’[événement de notification](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A) :</span><span class="sxs-lookup"><span data-stu-id="01d82-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="01d82-151">**Info-bulles pour l’accès par clavier**</span><span class="sxs-lookup"><span data-stu-id="01d82-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="01d82-152">Dans les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, pour déclencher une [info-bulle](xref:System.Windows.Forms.ToolTip) de contrôle en vue de son affichage, vous devez déplacer le pointeur de la souris dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="01d82-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="01d82-153">À compter de .NET Framework 4.8, un utilisateur de clavier peut déclencher l’info-bulle d’un contrôle en apportant le focus sur le contrôle à l’aide d’une touche tabulation ou de touches de direction, avec ou sans touches de modification.</span><span class="sxs-lookup"><span data-stu-id="01d82-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="01d82-154">Cette amélioration de l’accessibilité nécessite un autre [commutateur AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) :</span><span class="sxs-lookup"><span data-stu-id="01d82-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="01d82-155">La figure suivante montre l’info-bulle lorsque l’utilisateur a sélectionné un bouton à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Capture d’écran de l’info-bulle lorsque l’utilisateur accède à un bouton à l’aide du clavier.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="01d82-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="01d82-158">Dans .NET Framework 4.8, WPF comprend plusieurs améliorations d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="01d82-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="01d82-159">**Les narrateurs d’écran n’annoncent plus les éléments réduits ou masqués**</span><span class="sxs-lookup"><span data-stu-id="01d82-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="01d82-160">Les éléments réduits ou masqués (Collapsed ou Hidden) ne sont plus annoncés par le lecteur d’écran.</span><span class="sxs-lookup"><span data-stu-id="01d82-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="01d82-161">Les interfaces utilisateur qui contiennent des éléments avec une visibilité <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> ou <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> peuvent être mal représentées par les lecteurs d’écran si ces éléments sont annoncés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="01d82-162">Dans .NET Framework 4.8, WPF n’inclut plus les éléments réduits ou masqués dans l’affichage de contrôle de l’arborescence UIAutomation. Les lecteurs d’écran ne peuvent donc plus annoncer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="01d82-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="01d82-163">**Propriété SelectionTextBrush à utiliser avec une sélection de texte sans ornement**</span><span class="sxs-lookup"><span data-stu-id="01d82-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="01d82-164">Dans .NET Framework 4.7.2, WPF permet désormais de dessiner une sélection de texte <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.PasswordBox> sans utiliser la couche d’ornement.</span><span class="sxs-lookup"><span data-stu-id="01d82-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="01d82-165">Dans ce scénario, la couleur de premier plan du texte sélectionné a été dictée par <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="01d82-166">.NET Framework 4.8 comprend une nouvelle propriété (`SelectionTextBrush`) qui permet aux développeurs de sélectionner le pinceau du texte sélectionné lors de l’utilisation d’une sélection de texte sans ornement.</span><span class="sxs-lookup"><span data-stu-id="01d82-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="01d82-167">Cette propriété fonctionne uniquement avec les contrôles dérivés de <xref:System.Windows.Controls.Primitives.TextBoxBase> et avec le contrôle <xref:System.Windows.Controls.PasswordBox>des applications WPF où la sélection de texte sans ornement est activée.</span><span class="sxs-lookup"><span data-stu-id="01d82-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="01d82-168">Elle ne fonctionne pas avec le contrôle <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="01d82-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="01d82-169">Si la sélection de texte sans ornement n’est pas activée, cette propriété est ignorée.</span><span class="sxs-lookup"><span data-stu-id="01d82-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="01d82-170">Pour utiliser cette propriété, il suffit de l’ajouter à votre code XAML et d’utiliser le pinceau ou la liaison appropriés.</span><span class="sxs-lookup"><span data-stu-id="01d82-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="01d82-171">La sélection de texte qui en résulte ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="01d82-171">The resulting text selection looks like this:</span></span>

![Capture d’écran de l’application en cours d’exécution avec les mots Hello World sélectionnés.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="01d82-173">Vous pouvez combiner l’utilisation des propriétés `SelectionBrush` et `SelectionTextBrush` pour générer la combinaison de couleurs de premier plan et d’arrière-plan qui vous convient.</span><span class="sxs-lookup"><span data-stu-id="01d82-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="01d82-174">**Prise en charge de la propriété ControllerFor UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="01d82-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="01d82-175">La propriété `ControllerFor` d’UIAutomation retourne un tableau d’éléments d’automation manipulés par l’élément d’automation qui prend en charge cette propriété.</span><span class="sxs-lookup"><span data-stu-id="01d82-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="01d82-176">Cette propriété est couramment utilisée pour la suggestion automatique.</span><span class="sxs-lookup"><span data-stu-id="01d82-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="01d82-177">`ControllerFor` est utilisé lorsqu’un élément automation affecte un ou plusieurs segments de l’interface utilisateur de l’application ou du bureau.</span><span class="sxs-lookup"><span data-stu-id="01d82-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="01d82-178">Sinon, il est difficile d’associer l’impact de l’opération de contrôle aux éléments de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="01d82-179">Cette fonctionnalité permet aux contrôles de fournir une valeur pour la propriété `ControllerFor`.</span><span class="sxs-lookup"><span data-stu-id="01d82-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="01d82-180">.NET Framework 4.8 comprend une nouvelle méthode virtuelle : <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-181">Si vous souhaitez fournir une valeur pour la propriété `ControllerFor`, substituez cette méthode et retournez un `List<AutomationPeer>` pour les contrôles actuellement manipulés par ce <xref:System.Windows.Automation.Peers.AutomationPeer> :</span><span class="sxs-lookup"><span data-stu-id="01d82-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="01d82-182">**Info-bulles pour l’accès par clavier**</span><span class="sxs-lookup"><span data-stu-id="01d82-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="01d82-183">Dans .NET Framework 4.7.2 et versions antérieures, les info-bulles s’affichent uniquement lorsque l’utilisateur pointe la souris sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="01d82-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="01d82-184">Dans .NET Framework 4.8, les info-bulles s’affichent également dans le focus clavier et via un raccourci clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="01d82-185">Pour activer cette fonctionnalité, une application doit cibler .NET Framework 4,8 ou s’abonner à l’aide des commutateurs [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.UseLegacyAccessibilityFeatures.3` et `Switch.UseLegacyToolTipDisplay`.</span><span class="sxs-lookup"><span data-stu-id="01d82-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="01d82-186">Voici un exemple de fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="01d82-186">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="01d82-187">Une fois activée, tous les contrôles qui contiennent une info-bulle l’affichent dès que le contrôle reçoit le focus clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="01d82-188">L’info-bulle peut être ignorée au bout d’un certain temps ou lorsque le focus clavier est modifié.</span><span class="sxs-lookup"><span data-stu-id="01d82-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="01d82-189">Les utilisateurs peuvent également ignorer l’info-bulle manuellement à l’aide d’un nouveau raccourci clavier : Ctrl + Maj + F10.</span><span class="sxs-lookup"><span data-stu-id="01d82-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="01d82-190">Une fois que l’info-bulle a été ignorée, celle-ci peut être affichée à nouveau à l’aide du même raccourci clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="01d82-191">Les [info-bulles de ruban](xref:System.Windows.Controls.Ribbon.RibbonToolTip) des contrôles <xref:System.Windows.Controls.Ribbon.Ribbon> ne s’affichent pas dans le focus clavier. Elles s’affichent uniquement via le raccourci clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="01d82-192">**Prise en charge pour des propriétés SizeOfSet et PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="01d82-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="01d82-193">Windows 10 comprend deux nouvelles propriétés UIAutomation (`SizeOfSet` et `PositionInSet`) qui sont utilisées par les applications pour indiquer le nombre d’éléments que contient un ensemble.</span><span class="sxs-lookup"><span data-stu-id="01d82-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="01d82-194">Les applications clientes UIAutomation telles que les lecteurs d’écran peuvent ensuite interroger une application concernant ces propriétés, et annoncer une représentation exacte de l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="01d82-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="01d82-195">Dans .NET Framework 4.8, WPF expose ces deux propriétés à UIAutomation dans les applications WPF.</span><span class="sxs-lookup"><span data-stu-id="01d82-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="01d82-196">Cette opération peut se faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="01d82-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="01d82-197">En utilisant des propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="01d82-197">By using dependency properties.</span></span>

  <span data-ttu-id="01d82-198">WPF comprend deux nouvelles propriétés de dépendance : <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-199">Un développeur peut utiliser du code XAML pour définir les valeurs :</span><span class="sxs-lookup"><span data-stu-id="01d82-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="01d82-200">En substituant les méthodes virtuelles AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="01d82-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="01d82-201">Les méthodes virtuelles <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> et <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> ont été ajoutées à la classe AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="01d82-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="01d82-202">Un développeur peut fournir des valeurs pour `SizeOfSet` et `PositionInSet` en remplaçant ces méthodes, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="01d82-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="01d82-203">En outre, les éléments des instances <xref:System.Windows.Controls.ItemsControl> fournissent automatiquement une valeur pour ces propriétés, sans autre action nécessaire de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="01d82-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="01d82-204">Si un <xref:System.Windows.Controls.ItemsControl> est regroupé, la collection de groupes est représentée comme un ensemble, et chaque groupe est comptabilisé comme un ensemble distinct. Chaque élément du groupe fournit sa position à l’intérieur de celui-ci, ainsi que la taille du groupe.</span><span class="sxs-lookup"><span data-stu-id="01d82-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="01d82-205">Les valeurs automatiques ne sont pas affectées par la virtualisation.</span><span class="sxs-lookup"><span data-stu-id="01d82-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="01d82-206">Même si un élément n’est pas réalisé, il est comptabilisé dans la taille totale de l’ensemble, et affecte la position de ses éléments frères dans l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="01d82-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="01d82-207">Les valeurs automatiques sont fournies uniquement si l’application cible .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="01d82-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="01d82-208">Pour les applications qui ciblent une version antérieure du .NET Framework, vous pouvez définir le [commutateur `Switch.UseLegacyAccessibilityFeatures.3` AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), comme indiqué dans le fichier app. config suivant :</span><span class="sxs-lookup"><span data-stu-id="01d82-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="01d82-209">Concepteur de flux de travail Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="01d82-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="01d82-210">Dans .NET Framework 4.8, les modifications suivantes ont été apportées au concepteur de flux de travail :</span><span class="sxs-lookup"><span data-stu-id="01d82-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="01d82-211">Les utilisateurs qui utilisent le narrateur constateront des améliorations au niveau des étiquettes case FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="01d82-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="01d82-212">Les utilisateurs qui utilisent le narrateur constateront des améliorations au niveau des descriptions des boutons.</span><span class="sxs-lookup"><span data-stu-id="01d82-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="01d82-213">Les utilisateurs qui choisissent des thèmes à contraste élevé verront des améliorations de la visibilité du Concepteur de flux de travail et de ses contrôles, notamment de meilleurs ratios de contraste entre les éléments et des zones de sélection plus visibles utilisées pour les éléments actifs.</span><span class="sxs-lookup"><span data-stu-id="01d82-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="01d82-214">Si votre application cible .NET Framework 4.7.2 ou une version antérieure, vous pouvez choisir ces modifications en définissant le [commutateur `Switch.UseLegacyAccessibilityFeatures.3` AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) sur `false` dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="01d82-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="01d82-215">Pour plus d’informations, consultez la section [Activation des nouvelles fonctionnalités d’accessibilité](#taking-advantage-of-accessibility-enhancements) de cet article.</span><span class="sxs-lookup"><span data-stu-id="01d82-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="01d82-216">Nouveautés concernant l’accessibilité dans .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="01d82-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="01d82-217">.NET Framework 4.7.2 apporte de nouvelles fonctionnalités d’accessibilité dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="01d82-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="01d82-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="01d82-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-220">Windows Forms</span></span>

<span data-ttu-id="01d82-221">**Couleurs définies par le système d’exploitation dans les thèmes à contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="01d82-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="01d82-222">À compter de .NET Framework 4.7.2, Windows Forms utilise les couleurs définies par le système d’exploitation dans les thèmes à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="01d82-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="01d82-223">Cela concerne les contrôles suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-223">This affects the following controls:</span></span>

- <span data-ttu-id="01d82-224">Flèche déroulante du contrôle <xref:System.Windows.Forms.ToolStripDropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="01d82-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="01d82-225">Contrôles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> et <xref:System.Windows.Forms.CheckBox> dont la propriété <xref:System.Windows.Forms.ButtonBase.FlatStyle> est définie sur <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-226">Auparavant, les couleurs du texte sélectionné et de l’arrière-plan étaient sans contraste, ce qui nuisait à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="01d82-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="01d82-227">Contrôles contenus dans un <xref:System.Windows.Forms.GroupBox> dont la propriété <xref:System.Windows.Forms.Control.Enabled> est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="01d82-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="01d82-228">Contrôles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> et <xref:System.Windows.Forms.ToolStripDropDownButton> ayant un ratio contraste/luminosité accru dans le mode à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="01d82-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="01d82-229">Propriété <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> de <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="01d82-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="01d82-230">**Améliorations du Narrateur**</span><span class="sxs-lookup"><span data-stu-id="01d82-230">**Narrator improvements**</span></span>

<span data-ttu-id="01d82-231">.NET Framework 4.7.2 et les versions ultérieures améliorent la prise en charge du narrateur de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="01d82-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="01d82-232">Le Narrateur annonce la valeur de la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quand il annonce le texte d’un <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="01d82-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="01d82-233">Il indique quand un <xref:System.Windows.Forms.ToolStripMenuItem> a sa propriété <xref:System.Windows.Forms.Control.Enabled> définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="01d82-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="01d82-234">Il fournit des commentaires sur l’état d’une case à cocher quand la propriété <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> est définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="01d82-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="01d82-235">L’ordre de focus du mode balayage du Narrateur est cohérent avec l’ordre d’affichage des contrôles dans la fenêtre de la boîte de dialogue de téléchargement ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="01d82-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="01d82-236">**Améliorations du contrôle DataGridView**</span><span class="sxs-lookup"><span data-stu-id="01d82-236">**DataGridView improvements**</span></span>

<span data-ttu-id="01d82-237">À compter de .NET Framework 4.7.2, le contrôle <xref:System.Windows.Forms.DataGridView> présente les améliorations d’accessibilité suivantes :</span><span class="sxs-lookup"><span data-stu-id="01d82-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="01d82-238">Les lignes peuvent être triées à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="01d82-239">Un utilisateur peut utiliser la touche F3 pour trier la colonne active.</span><span class="sxs-lookup"><span data-stu-id="01d82-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="01d82-240">Quand <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> est défini sur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, l’en-tête de colonne change de couleur pour indiquer la colonne active quand l’utilisateur se déplace entre les cellules de la ligne active à l’aide de la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="01d82-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="01d82-241">La propriété <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> d’un <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> retourne le bon contrôle parent.</span><span class="sxs-lookup"><span data-stu-id="01d82-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="01d82-242">**Amélioration des signaux visuels**</span><span class="sxs-lookup"><span data-stu-id="01d82-242">**Improved visual cues**</span></span>

- <span data-ttu-id="01d82-243">Les contrôles <xref:System.Windows.Forms.RadioButton> et <xref:System.Windows.Forms.CheckBox> avec une propriété <xref:System.Windows.Forms.ButtonBase.Text> vide affichent un indicateur de focus quand ils deviennent actifs.</span><span class="sxs-lookup"><span data-stu-id="01d82-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="01d82-244">**Prise en charge améliorée de la grille des propriétés**</span><span class="sxs-lookup"><span data-stu-id="01d82-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="01d82-245">Les éléments enfants du contrôle <xref:System.Windows.Forms.PropertyGrid> retournent désormais un `true` pour la propriété <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> uniquement quand un élément PropertyGrid est activé.</span><span class="sxs-lookup"><span data-stu-id="01d82-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="01d82-246">Les éléments enfants du contrôle <xref:System.Windows.Forms.PropertyGrid> retournent un `false` pour la propriété <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> uniquement quand un élément PropertyGrid peut être changé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="01d82-247">**Navigation au clavier améliorée**</span><span class="sxs-lookup"><span data-stu-id="01d82-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="01d82-248">Le contrôle <xref:System.Windows.Forms.ToolStripButton> peut être activé quand il est contenu dans un <xref:System.Windows.Forms.ToolStripPanel> dont la propriété <xref:System.Windows.Forms.ToolStripPanel.TabStop> a la valeur `true`</span><span class="sxs-lookup"><span data-stu-id="01d82-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="01d82-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="01d82-250">**Changements apportés aux contrôles CheckBox et RadioButton**</span><span class="sxs-lookup"><span data-stu-id="01d82-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="01d82-251">Dans .NET Framework 4.7.1 et les versions antérieures, les contrôles WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> et <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ont des visuels de focus incohérents et, dans les thèmes standard et à contraste élevé, des visuels de focus inappropriés.</span><span class="sxs-lookup"><span data-stu-id="01d82-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="01d82-252">Ces problèmes se produisent dans les cas où les contrôles n’ont pas de contenu défini.</span><span class="sxs-lookup"><span data-stu-id="01d82-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="01d82-253">Cela peut rendre la transition entre les thèmes confuse et le visuel de focus difficile à voir.</span><span class="sxs-lookup"><span data-stu-id="01d82-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="01d82-254">Dans .NET Framework 4.7.2, ces visuels sont désormais plus cohérents entre les thèmes et plus facilement visibles dans les thèmes de type classique et à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="01d82-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="01d82-255">**Contrôles WinForms hébergés dans une application WPF**</span><span class="sxs-lookup"><span data-stu-id="01d82-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="01d82-256">Dans .NET Framework 4.7.1 et les versions antérieures, les contrôles WinForms hébergés dans une application WPF ne permettaient pas aux utilisateurs de sortir de la couche WinForms à l’aide de la touche de tabulation quand le contrôle WPF <xref:System.Windows.Forms.Integration.ElementHost> était le premier ou le dernier contrôle de cette couche.</span><span class="sxs-lookup"><span data-stu-id="01d82-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="01d82-257">Dans .NET Framework 4.7.2, les utilisateurs peuvent désormais sortir de la couche WinForms à l’aide de la touche de tabulation.</span><span class="sxs-lookup"><span data-stu-id="01d82-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="01d82-258">Toutefois, les applications automatisées qui s’attendent à ce que le focus ne quitte jamais la couche WinForms risquent de ne plus fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="01d82-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="01d82-259">Nouveautés concernant l’accessibilité dans .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="01d82-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="01d82-260">.NET Framework 4.7.1 apporte de nouvelles fonctionnalités d’accessibilité dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="01d82-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="01d82-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="01d82-263">Contrôles web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="01d82-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="01d82-264">Outils du kit SDK .NET</span><span class="sxs-lookup"><span data-stu-id="01d82-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="01d82-265">Concepteur de flux de travail Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="01d82-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="01d82-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="01d82-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="01d82-267">**Améliorations du lecteur d’écran**</span><span class="sxs-lookup"><span data-stu-id="01d82-267">**Screen reader improvements**</span></span>

<span data-ttu-id="01d82-268">Si les améliorations apportées à l’accessibilité sont activées, .NET Framework 4.7.1 inclut les améliorations suivantes qui affectent les lecteurs d’écran :</span><span class="sxs-lookup"><span data-stu-id="01d82-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="01d82-269">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.Expander> étaient annoncés par des lecteurs d’écran sous forme de boutons.</span><span class="sxs-lookup"><span data-stu-id="01d82-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="01d82-270">À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que groupes extensibles/réductibles.</span><span class="sxs-lookup"><span data-stu-id="01d82-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="01d82-271">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.DataGridCell> étaient annoncés par des lecteurs d’écran comme étant « personnalisés ».</span><span class="sxs-lookup"><span data-stu-id="01d82-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="01d82-272">À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que cellule de grille de données (localisée).</span><span class="sxs-lookup"><span data-stu-id="01d82-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="01d82-273">À compter de .NET Framework 4.7.1, les lecteurs d’écran annoncent le nom d’un élément <xref:System.Windows.Controls.ComboBox> modifiable.</span><span class="sxs-lookup"><span data-stu-id="01d82-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="01d82-274">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.PasswordBox> entraînaient l’annonce « Aucun élément dans la vue » ou avaient un comportement incorrect.</span><span class="sxs-lookup"><span data-stu-id="01d82-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="01d82-275">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="01d82-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="01d82-276">**Prise en charge de zones dynamiques UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="01d82-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="01d82-277">Les lecteurs d’écran tels que le Narrateur aident les personnes à lire le contenu de l’interface utilisateur d’une application, généralement par une sortie conversion de texte par synthèse vocale du contenu de l’interface utilisateur actif.</span><span class="sxs-lookup"><span data-stu-id="01d82-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="01d82-278">Toutefois, si un élément d’interface utilisateur change et n’est pas actif, l’utilisateur peut ne pas en être informé et manquer des informations importantes.</span><span class="sxs-lookup"><span data-stu-id="01d82-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="01d82-279">Les zones dynamiques visent à résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="01d82-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="01d82-280">Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client UIAutomation qu’une modification importante a été apportée à un élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="01d82-281">Le lecteur d’écran peut ensuite décider comment et quand informer l’utilisateur de cette modification.</span><span class="sxs-lookup"><span data-stu-id="01d82-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="01d82-282">Pour prendre en charge les zones dynamiques, les API suivantes ont été ajoutées à WPF :</span><span class="sxs-lookup"><span data-stu-id="01d82-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="01d82-283">Champs <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, qui identifient la propriété **LiveSetting** et l’événement **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="01d82-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="01d82-284">Il peuvent être définis à l’aide de XAML.</span><span class="sxs-lookup"><span data-stu-id="01d82-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="01d82-285">Propriété jointe **AutomationProperties.LiveSetting**, qui informe le lecteur d’écran de l’importance de la modification de l’interface utilisateur pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="01d82-286">Propriété <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, qui identifie la propriété jointe **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="01d82-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="01d82-287">Méthode <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, qui peut être remplacée pour fournir une valeur **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="01d82-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="01d82-288">Méthodes <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, qui obtiennent et définissent une valeur **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="01d82-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="01d82-289">Énumération <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, qui définit les valeurs **LiveSetting** possibles suivantes :</span><span class="sxs-lookup"><span data-stu-id="01d82-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="01d82-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-291">L’élément n’envoie pas de notification si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="01d82-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="01d82-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-293">L’élément envoie des notifications qui ne provoquent pas d’interruption si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="01d82-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="01d82-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d82-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01d82-295">L’élément envoie des notifications qui provoquent des interruptions si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="01d82-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="01d82-296">Vous pouvez créer une zone dynamique en définissant la propriété **AutomationProperties.LiveSetting** sur l’élément qui vous intéresse, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="01d82-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="01d82-297">Quand les données de la zone dynamique sont modifiées et que vous devez informer un lecteur d’écran, vous déclenchez explicitement un événement, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="01d82-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="01d82-298">**Contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="01d82-298">**High contrast**</span></span>

<span data-ttu-id="01d82-299">À compter de .NET Framework 4.7.1, des améliorations ont été apportées au niveau du contraste élevé pour différents contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="01d82-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="01d82-300">Elles sont désormais visibles quand le thème <xref:System.Windows.SystemParameters.HighContrast%2A> est défini.</span><span class="sxs-lookup"><span data-stu-id="01d82-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="01d82-301">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="01d82-301">These include:</span></span>

- <span data-ttu-id="01d82-302">Contrôle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="01d82-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="01d82-303">L’élément visuel de focus pour le contrôle <xref:System.Windows.Controls.Expander> est désormais visible.</span><span class="sxs-lookup"><span data-stu-id="01d82-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="01d82-304">Les éléments visuels de clavier pour les contrôles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.RadioButton> sont également visibles.</span><span class="sxs-lookup"><span data-stu-id="01d82-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="01d82-305">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-305">For example:</span></span>

  <span data-ttu-id="01d82-306">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-306">Before:</span></span> 

  ![Capture d’écran du contrôle Expander avec focus et aucun visuel focus.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="01d82-308">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-308">After:</span></span> 

  ![Capture d’écran du contrôle Expander avec focus montrant une ligne en pointillés autour du texte du contrôle.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="01d82-310">Contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="01d82-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="01d82-311">Le texte dans les contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> est désormais plus facile à voir quand il est sélectionné dans les thèmes à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="01d82-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="01d82-312">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-312">For example:</span></span>

  <span data-ttu-id="01d82-313">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-313">Before:</span></span> 

  ![Capture d’écran des boutons radio et check avec une mauvaise visibilité du texte sur les thèmes à contraste élevé.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="01d82-315">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-315">After:</span></span> 

  ![Capture d’écran des boutons radio et check avec une meilleure visibilité du texte sur les thèmes à contraste élevé.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="01d82-317">Contrôle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="01d82-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="01d82-318">À compter de .NET Framework 4.7.1, la bordure d’un contrôle <xref:System.Windows.Controls.ComboBox> désactivé est de la même couleur que le texte désactivé.</span><span class="sxs-lookup"><span data-stu-id="01d82-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="01d82-319">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-319">For example:</span></span>

  <span data-ttu-id="01d82-320">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-320">Before:</span></span> 

  ![Capture d’écran d’une zone de liste déroulante désactivée avec bordure et texte de contrôle dans différentes couleurs.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="01d82-322">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-322">After:</span></span>   

  ![Capture d’écran d’une zone de liste déroulante désactivée avec la même couleur que le texte du contrôle.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="01d82-324">En outre, les boutons désactivés et actifs utilisent la couleur de thème correcte.</span><span class="sxs-lookup"><span data-stu-id="01d82-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="01d82-325">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-325">Before:</span></span>

  ![Capture d’écran d’un bouton noir avec du texte gris indiquant me concentrer.](./media/whats-new-in-accessibility/button-theme-colors-before.png) 

  <span data-ttu-id="01d82-327">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-327">After:</span></span> 

  ![Capture d’écran d’un bouton bleu avec du texte noir indiquant me concentrer.](./media/whats-new-in-accessibility/button-theme-colors-after.png) 

  <span data-ttu-id="01d82-329">Enfin, dans .NET Framework 4.7 et versions antérieures, la définition du style d’un contrôle <xref:System.Windows.Controls.ComboBox> sur `Toolbar.ComboBoxStyleKey` rendait la flèche déroulante invisible.</span><span class="sxs-lookup"><span data-stu-id="01d82-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="01d82-330">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="01d82-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="01d82-331">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-331">For example:</span></span>

  <span data-ttu-id="01d82-332">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-332">Before:</span></span> 

  ![Capture d’écran d’un contrôle de zone de liste déroulante avec une flèche de déroulement invisible.](./media/whats-new-in-accessibility/combo-box-style-key-before.png) 

  <span data-ttu-id="01d82-334">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-334">After:</span></span> 

  ![Capture d’écran d’un contrôle ComBoxBox affichant la flèche déroulante.](./media/whats-new-in-accessibility/combo-box-style-key-after.png) 

- <span data-ttu-id="01d82-336">Contrôle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="01d82-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="01d82-337">À compter de .NET Framework 4.7.1, la flèche d’indicateur de tri dans les contrôles <xref:System.Windows.Controls.DataGrid> utilise maintenant les couleurs de thème correctes.</span><span class="sxs-lookup"><span data-stu-id="01d82-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="01d82-338">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-338">For example:</span></span>

  <span data-ttu-id="01d82-339">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-339">Before:</span></span> 

  ![Capture d’écran de la flèche d’indicateur de tri avant les améliorations.](./media/whats-new-in-accessibility/sort-indicator-before.png) 

  <span data-ttu-id="01d82-341">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-341">After:</span></span>   

  ![Capture d’écran de la flèche d’indicateur de tri après les améliorations.](./media/whats-new-in-accessibility/sort-indicator-after.png) 

  <span data-ttu-id="01d82-343">En outre, dans .NET Framework 4.7 et versions antérieures, le style de lien par défaut prenait une couleur incorrecte lorsque l’utilisateur pointait avec la souris dans des modes de contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="01d82-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="01d82-344">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="01d82-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="01d82-345">De même, depuis .NET Framework 4.7.1, les colonnes de cases à cocher <xref:System.Windows.Controls.DataGrid> utilisent les couleurs attendues pour les commentaires de focus clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="01d82-346">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-346">Before:</span></span> 

  ![Capture d’écran d’un lien indiquant click me !](./media/whats-new-in-accessibility/default-link-style-before.png) 

  <span data-ttu-id="01d82-349">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-349">After:</span></span>    

  ![Capture d’écran d’un lien indiquant click me !](./media/whats-new-in-accessibility/default-link-style-after.png) 

<span data-ttu-id="01d82-352">Pour plus d’informations sur les améliorations apportées à l’accessibilité WPF dans .NET Framework 4.7.1, consultez [Améliorations apportées à l’accessibilité dans WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="01d82-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="01d82-353">Améliorations apportées à l’accessibilité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d82-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="01d82-354">Dans .NET Framework 4.7.1, WinForms (Windows Forms) présente des modifications de l’accessibilité dans les domaines suivants.</span><span class="sxs-lookup"><span data-stu-id="01d82-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="01d82-355">**Affichage amélioré en mode de contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="01d82-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="01d82-356">À compter de .NET Framework 4.7.1, différents contrôles WinForms offrent un meilleur rendu dans les modes de contraste élevé disponibles dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="01d82-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="01d82-357">Windows 10 a modifié les valeurs de certaines couleurs système à contraste élevé et Windows Forms repose sur le framework Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="01d82-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="01d82-358">Pour une expérience optimale, procédez à une exécution sur la dernière version de Windows et activez les dernières modifications du système d’exploitation en ajoutant un fichier app.manifest dans une application de test et supprimez les marques de commentaire de la ligne de système d’exploitation Windows 10 pour qu’elle ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="01d82-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="01d82-359">Voici quelques exemples de modifications du contraste élevé :</span><span class="sxs-lookup"><span data-stu-id="01d82-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="01d82-360">Les coches dans les éléments <xref:System.Windows.Forms.MenuStrip> sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="01d82-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="01d82-361">Quand ils sont sélectionnés, les éléments <xref:System.Windows.Forms.MenuStrip> désactivés sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="01d82-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="01d82-362">Le texte dans un contrôle <xref:System.Windows.Forms.Button> sélectionné contraste avec la couleur de sélection.</span><span class="sxs-lookup"><span data-stu-id="01d82-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="01d82-363">Le texte désactivé est plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="01d82-363">Disabled text is easier to read.</span></span> <span data-ttu-id="01d82-364">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="01d82-364">For example:</span></span>

  <span data-ttu-id="01d82-365">Avant :</span><span class="sxs-lookup"><span data-stu-id="01d82-365">Before:</span></span>

  ![Capture d’écran d’une application qui utilise des contrôles différents exécutés en mode de contraste élevé avant les améliorations de l’accessibilité.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png) 

  <span data-ttu-id="01d82-367">Après :</span><span class="sxs-lookup"><span data-stu-id="01d82-367">After:</span></span>

  ![Capture d’écran d’une application qui utilise différents contrôles exécutés en mode de contraste élevé après des améliorations de l’accessibilité.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png) 

- <span data-ttu-id="01d82-369">Améliorations du contraste élevé dans la boîte de dialogue Thread Exception (Exception de thread).</span><span class="sxs-lookup"><span data-stu-id="01d82-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="01d82-370">**Prise en charge améliorée du Narrateur**</span><span class="sxs-lookup"><span data-stu-id="01d82-370">**Improved Narrator support**</span></span>

<span data-ttu-id="01d82-371">Dans .NET Framework 4.7.1, Windows Forms inclut les améliorations suivantes au niveau de l’accessibilité du narrateur :</span><span class="sxs-lookup"><span data-stu-id="01d82-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="01d82-372">Le contrôle <xref:System.Windows.Forms.MonthCalendar> est accessible par le Narrateur, ainsi que par d’autres outils UI Automation.</span><span class="sxs-lookup"><span data-stu-id="01d82-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="01d82-373">Le contrôle <xref:System.Windows.Forms.CheckedListBox> avertit le Narrateur quand l’état de case à cocher d’un élément a changé pour que l’utilisateur sache que la valeur d’un élément de liste est modifiée.</span><span class="sxs-lookup"><span data-stu-id="01d82-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="01d82-374">Le contrôle <xref:System.Windows.Forms.DataGridViewCell> signale l’état Lecture seule correct au Narrateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="01d82-375">Le Narrateur peut désormais lire le texte <xref:System.Windows.Forms.ToolStripMenuItem> désactivé, alors qu’il ignorait précédemment les éléments de menu désactivés.</span><span class="sxs-lookup"><span data-stu-id="01d82-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="01d82-376">**Prise en charge améliorée des modèles d’accessibilité UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="01d82-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="01d82-377">À compter de .NET Framework 4.7.1, les développeurs d’outils technologiques d’accessibilité peuvent tirer parti des modèles d’accessibilité d’API courants et des propriétés de plusieurs contrôles WinForms.</span><span class="sxs-lookup"><span data-stu-id="01d82-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="01d82-378">Ces améliorations en matière d’accessibilité sont notamment :</span><span class="sxs-lookup"><span data-stu-id="01d82-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="01d82-379"><xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ToolStripSplitButton> prennent maintenant en charge le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="01d82-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="01d82-380"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend maintenant en charge le [modèle Basculer](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="01d82-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="01d82-381">Le contrôle <xref:System.Windows.Forms.ToolStripItem> prend en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> et le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="01d82-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="01d82-382">Les contrôles <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> prennent en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="01d82-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="01d82-383">**Expérience améliorée avec l’Explorateur de propriétés**</span><span class="sxs-lookup"><span data-stu-id="01d82-383">**Improved property browser experience**</span></span>

<span data-ttu-id="01d82-384">À compter de .NET Framework 4.7.1, Windows Forms propose :</span><span class="sxs-lookup"><span data-stu-id="01d82-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="01d82-385">Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="01d82-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="01d82-386">Une réduction des taquets de tabulation inutiles.</span><span class="sxs-lookup"><span data-stu-id="01d82-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="01d82-387">Des rapports plus élaborés sur les types de contrôles.</span><span class="sxs-lookup"><span data-stu-id="01d82-387">Better reporting of control types.</span></span>
- <span data-ttu-id="01d82-388">Un comportement amélioré du Narrateur.</span><span class="sxs-lookup"><span data-stu-id="01d82-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="01d82-389">Contrôles web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="01d82-389">ASP.NET web controls</span></span>

<span data-ttu-id="01d82-390">À compter de .NET Framework 4.7.1 et de Visual Studio 2017 version 15,3, ASP.NET améliore le fonctionnement des contrôles Web ASP.NET avec la technologie d’accessibilité dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="01d82-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="01d82-391">Les changements apportés sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-391">Changes include the following:</span></span>

- <span data-ttu-id="01d82-392">Changements visant à implémenter les modèles d’accessibilité de l’interface utilisateur manquants dans les contrôles, comme la boîte de dialogue **Ajouter un champ** de l’Assistant **Vue Détails** ou la boîte de dialogue **Configurer ListView** de l’Assistant **ListView**.</span><span class="sxs-lookup"><span data-stu-id="01d82-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="01d82-393">Changements visant à améliorer l’affichage en mode de contraste élevé, comme **l’éditeur de champs du pagineur de données**.</span><span class="sxs-lookup"><span data-stu-id="01d82-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="01d82-394">Changements visant à améliorer les expériences de navigation au clavier pour les contrôles, comme la boîte de dialogue **Champs** de l’Assistant **Modifier les champs du pagineur** du contrôle DataPager, la boîte de dialogue **Configurer ObjectContext** ou la boîte de dialogue **Configurer la sélection de données** de l’Assistant **Configurer la source de données**.</span><span class="sxs-lookup"><span data-stu-id="01d82-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="01d82-395">Outils du kit SDK . NET</span><span class="sxs-lookup"><span data-stu-id="01d82-395">.NET SDK Tools</span></span>

<span data-ttu-id="01d82-396">Divers problèmes d’accessibilité ont été corrigés dans [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) et [l’outil Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="01d82-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="01d82-397">La plupart étaient des problèmes sans gravité, par exemple, un nom non défini ou certains modèles d’automatisation de l’interface utilisateur non implémentés correctement.</span><span class="sxs-lookup"><span data-stu-id="01d82-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="01d82-398">La majorité des utilisateurs ne remarqueront même pas ces problèmes, mais les clients qui utilisent des technologies d’assistance comme les lecteurs d’écran trouveront les outils de ce kit SDK plus accessibles.</span><span class="sxs-lookup"><span data-stu-id="01d82-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="01d82-399">Ces améliorations changent certains comportements précédents, comme l’ordre de focus du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="01d82-400">Concepteur de flux de travail Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="01d82-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="01d82-401">Les changements apportés pour améliorer l’accessibilité dans le Concepteur de flux de travail sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="01d82-402">L’ordre de tabulation est maintenant de gauche à droite et de haut en bas dans certains contrôles :</span><span class="sxs-lookup"><span data-stu-id="01d82-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="01d82-403">La fenêtre d’initialisation de la corrélation pour définir les données de corrélation pour l’activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="01d82-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="01d82-404">La fenêtre de définition du contenu pour les activités <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="01d82-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="01d82-405">D’autres fonctions sont disponibles par le biais du clavier :</span><span class="sxs-lookup"><span data-stu-id="01d82-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="01d82-406">Quand vous modifiez les propriétés d’une activité, les groupes de propriétés peuvent être réduits à l’aide du clavier la première fois qu’ils ont le focus.</span><span class="sxs-lookup"><span data-stu-id="01d82-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="01d82-407">Les icônes d’avertissement sont accessibles à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="01d82-408">Le bouton **Plus de propriétés** de la fenêtre **Propriétés** est accessible à l’aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="01d82-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="01d82-409">Les utilisateurs du clavier peuvent accéder aux éléments d’en-tête dans les volets **Arguments** et **Variables** du Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="01d82-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="01d82-410">Une meilleure visibilité des éléments ayant le focus, par exemple dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="01d82-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="01d82-411">Ajout de lignes dans des grilles de données utilisées par le Concepteur de flux de travail et les concepteurs d’activités.</span><span class="sxs-lookup"><span data-stu-id="01d82-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="01d82-412">Déplacement par tabulation dans les champs des activités <xref:System.ServiceModel.Activities.ReceiveReply> et <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="01d82-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="01d82-413">Définition de valeurs par défaut pour les variables ou les arguments</span><span class="sxs-lookup"><span data-stu-id="01d82-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="01d82-414">Les lecteurs d’écran peuvent désormais reconnaître correctement :</span><span class="sxs-lookup"><span data-stu-id="01d82-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="01d82-415">Les points d’arrêt définis dans le Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="01d82-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="01d82-416">Les activités <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> et <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="01d82-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="01d82-417">Le contenu de l’activité <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="01d82-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="01d82-418">Le type cible pour l’activité <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="01d82-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="01d82-419">Le contrôle zone de liste déroulante Exception et la section Finally de l’activité <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="01d82-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="01d82-420">Le contrôle zone de liste déroulante Type de message, le séparateur dans la fenêtre Ajouter des initialiseurs de corrélation, la fenêtre de définition du contenu et la fenêtre Définition de CorrelatesOn dans les activités de messagerie (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="01d82-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="01d82-421">Transitions d’ordinateur d’état et destination des transitions.</span><span class="sxs-lookup"><span data-stu-id="01d82-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="01d82-422">Annotations et connecteurs sur les activités <xref:System.Activities.Statements.FlowDecision>.</span><span class="sxs-lookup"><span data-stu-id="01d82-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="01d82-423">Les menus contextuels (accessibles en cliquant avec le bouton droit) pour les activités.</span><span class="sxs-lookup"><span data-stu-id="01d82-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="01d82-424">Les éditeurs de valeurs de propriété, le bouton Effacer la recherche, les boutons a catégorie par et boutons de tri Par catégorie et Ordre alphabétique et la boîte de dialogue Éditeur d’expressions dans la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="01d82-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="01d82-425">Le pourcentage de zoom dans le Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="01d82-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="01d82-426">Le séparateur dans les activités <xref:System.Activities.Statements.Parallel> et <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="01d82-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="01d82-427">L’activité <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="01d82-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="01d82-428">La fenêtre Sélectionner les types pour les activités de dictionnaire (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span><span class="sxs-lookup"><span data-stu-id="01d82-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="01d82-429">La fenêtre Rechercher et sélectionner un type .NET.</span><span class="sxs-lookup"><span data-stu-id="01d82-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="01d82-430">Les barres de navigation dans le Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="01d82-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="01d82-431">Les utilisateurs qui choisissent des thèmes à contraste élevé verront de nombreuses améliorations de la visibilité du Concepteur de flux de travail et de ses contrôles, notamment de meilleurs ratios de contraste entre les éléments et des zones de sélection plus visibles utilisées pour les éléments actifs.</span><span class="sxs-lookup"><span data-stu-id="01d82-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="01d82-432">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01d82-432">See also</span></span>

- [<span data-ttu-id="01d82-433">Nouveautés du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="01d82-433">What's new in the .NET Framework</span></span>](index.md)
