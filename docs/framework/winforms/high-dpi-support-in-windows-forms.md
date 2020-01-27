---
title: Prise en charge de la haute résolution
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a5c3125475c2de2cf83a3d97e356b26c0acdde99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741896"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="42e96-102">Prise en charge des résolutions élevées en Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42e96-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="42e96-103">À partir de la .NET Framework 4,7, Windows Forms comprend des améliorations pour les scénarios haute résolution et PPP dynamique courants.</span><span class="sxs-lookup"><span data-stu-id="42e96-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="42e96-104">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="42e96-104">These include:</span></span>

- <span data-ttu-id="42e96-105">Améliorations de la mise à l’échelle et de la disposition d’un certain nombre de contrôles Windows Forms, tels que le contrôle <xref:System.Windows.Forms.MonthCalendar> et le contrôle <xref:System.Windows.Forms.CheckedListBox>.</span><span class="sxs-lookup"><span data-stu-id="42e96-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="42e96-106">Mise à l’échelle à passage unique.</span><span class="sxs-lookup"><span data-stu-id="42e96-106">Single-pass scaling.</span></span>  <span data-ttu-id="42e96-107">Dans le .NET Framework 4,6 et les versions antérieures, la mise à l’échelle a été effectuée à travers plusieurs passes, ce qui a entraîné une mise à l’échelle de certains contrôles plus que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="42e96-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="42e96-108">Prise en charge des scénarios PPP dynamiques dans lesquels l’utilisateur modifie la résolution ou le facteur d’échelle après le lancement d’une application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="42e96-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="42e96-109">Dans les versions de la .NET Framework à partir de la .NET Framework 4,7, la prise en charge de la haute résolution améliorée est une fonctionnalité d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="42e96-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="42e96-110">Vous devez configurer votre application pour en tirer parti.</span><span class="sxs-lookup"><span data-stu-id="42e96-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="42e96-111">Configuration de votre application Windows Forms pour la prise en charge de la haute résolution</span><span class="sxs-lookup"><span data-stu-id="42e96-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="42e96-112">Les nouvelles fonctionnalités de Windows Forms qui prennent en charge la reconnaissance haute résolution sont uniquement disponibles dans les applications qui ciblent le .NET Framework 4,7 et qui s’exécutent sur des systèmes d’exploitation Windows à partir de Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="42e96-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="42e96-113">En outre, pour configurer la prise en charge des résolutions élevées dans votre application Windows Forms, vous devez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="42e96-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="42e96-114">Déclarer la compatibilité avec Windows 10.</span><span class="sxs-lookup"><span data-stu-id="42e96-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="42e96-115">Pour ce faire, ajoutez le code suivant à votre fichier manifeste :</span><span class="sxs-lookup"><span data-stu-id="42e96-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="42e96-116">Activez la reconnaissance de la résolution par moniteur dans le fichier *app. config* .</span><span class="sxs-lookup"><span data-stu-id="42e96-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="42e96-117">Windows Forms introduit un nouvel élément [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) pour prendre en charge les nouvelles fonctionnalités et personnalisations ajoutées à partir du .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="42e96-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="42e96-118">Pour tirer parti des nouvelles fonctionnalités qui prennent en charge la haute résolution, ajoutez ce qui suit à votre fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="42e96-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="42e96-119">Dans les versions précédentes de la .NET Framework, vous utilisiez le manifeste pour ajouter la prise en charge des résolutions élevées.</span><span class="sxs-lookup"><span data-stu-id="42e96-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="42e96-120">Cette approche n’est plus recommandée, car elle remplace les paramètres définis dans le fichier app. config.</span><span class="sxs-lookup"><span data-stu-id="42e96-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="42e96-121">Appelez la méthode statique <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="42e96-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="42e96-122">Il doit s’agir du premier appel de méthode dans le point d’entrée de votre application.</span><span class="sxs-lookup"><span data-stu-id="42e96-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="42e96-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="42e96-123">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="42e96-124">Désactivation des fonctionnalités haute résolution individuelles</span><span class="sxs-lookup"><span data-stu-id="42e96-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="42e96-125">La définition de la valeur `DpiAwareness` sur `PerMonitorV2` active toutes les fonctionnalités de reconnaissance haute résolution prises en charge par les versions de .NET Framework à partir de la .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="42e96-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="42e96-126">En règle générale, cela convient à la plupart des applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="42e96-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="42e96-127">Toutefois, vous souhaiterez peut-être refuser une ou plusieurs fonctionnalités individuelles.</span><span class="sxs-lookup"><span data-stu-id="42e96-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="42e96-128">La raison la plus importante pour cela est que votre code d’application existant gère déjà cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="42e96-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="42e96-129">Par exemple, si votre application gère la mise à l’échelle automatique, vous souhaiterez peut-être désactiver la fonctionnalité de redimensionnement automatique comme suit :</span><span class="sxs-lookup"><span data-stu-id="42e96-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="42e96-130">Pour obtenir la liste des clés individuelles et leurs valeurs, consultez [Windows Forms ajouter un élément de configuration](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="42e96-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="42e96-131">Nouveaux événements de modification DPI</span><span class="sxs-lookup"><span data-stu-id="42e96-131">New DPI change events</span></span>

<span data-ttu-id="42e96-132">À partir de la .NET Framework 4,7, trois nouveaux événements vous permettent de gérer par programmation les modifications PPP dynamiques :</span><span class="sxs-lookup"><span data-stu-id="42e96-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="42e96-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, qui est déclenché lorsque le paramètre DPI d’un contrôle est modifié par programme après qu’un événement de modification de PPP s’est produit pour son contrôle ou formulaire parent.</span><span class="sxs-lookup"><span data-stu-id="42e96-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="42e96-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, qui est déclenché lorsque le paramètre DPI d’un contrôle est modifié par programme avant qu’un événement de modification DPI pour son contrôle ou formulaire parent s’est produit.</span><span class="sxs-lookup"><span data-stu-id="42e96-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="42e96-135"><xref:System.Windows.Forms.Form.DpiChanged>, qui est déclenché lorsque le paramètre DPI change sur le périphérique d’affichage où le formulaire est actuellement affiché.</span><span class="sxs-lookup"><span data-stu-id="42e96-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="42e96-136">Nouvelles méthodes et propriétés d’assistance</span><span class="sxs-lookup"><span data-stu-id="42e96-136">New helper methods and properties</span></span>

<span data-ttu-id="42e96-137">La .NET Framework 4,7 ajoute également un certain nombre de nouvelles méthodes et propriétés d’assistance qui fournissent des informations sur la mise à l’échelle DPI et vous permettent d’effectuer une mise à l’échelle PPP.</span><span class="sxs-lookup"><span data-stu-id="42e96-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="42e96-138">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="42e96-138">These include:</span></span>

- <span data-ttu-id="42e96-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, qui convertit une valeur logique en pixels de périphérique.</span><span class="sxs-lookup"><span data-stu-id="42e96-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="42e96-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, qui met à l’échelle une image bitmap sur les DPI logiques pour un appareil.</span><span class="sxs-lookup"><span data-stu-id="42e96-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="42e96-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, qui retourne la valeur PPP de l’appareil actuel.</span><span class="sxs-lookup"><span data-stu-id="42e96-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="42e96-142">Considérations relatives au contrôle de version</span><span class="sxs-lookup"><span data-stu-id="42e96-142">Versioning considerations</span></span>

<span data-ttu-id="42e96-143">En plus de s’exécuter sur .NET Framework 4,7 et Windows 10 Creators Update, votre application peut également s’exécuter dans un environnement dans lequel elle n’est pas compatible avec les améliorations à haute résolution.</span><span class="sxs-lookup"><span data-stu-id="42e96-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="42e96-144">Dans ce cas, vous devez développer une solution de secours pour votre application.</span><span class="sxs-lookup"><span data-stu-id="42e96-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="42e96-145">Vous pouvez effectuer cette opération pour effectuer un [dessin personnalisé](./controls/user-drawn-controls.md) afin de gérer la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="42e96-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="42e96-146">Pour ce faire, vous devez également déterminer le système d’exploitation sur lequel votre application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="42e96-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="42e96-147">Vous pouvez le faire avec du code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="42e96-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="42e96-148">Notez que votre application ne détectera pas correctement Windows 10 si elle n’était pas listée en tant que système d’exploitation pris en charge dans le manifeste de l’application.</span><span class="sxs-lookup"><span data-stu-id="42e96-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="42e96-149">Vous pouvez également vérifier la version de la .NET Framework à laquelle l’application a été générée :</span><span class="sxs-lookup"><span data-stu-id="42e96-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="42e96-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42e96-150">See also</span></span>

- [<span data-ttu-id="42e96-151">Windows Forms ajouter un élément de configuration</span><span class="sxs-lookup"><span data-stu-id="42e96-151">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="42e96-152">Réglage de la taille et de l'échelle des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42e96-152">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
