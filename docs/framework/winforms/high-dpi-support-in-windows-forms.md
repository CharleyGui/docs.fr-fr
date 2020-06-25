---
title: Prise en charge de résolutions élevées
description: En savoir plus sur la prise en charge dans Windows Forms pour les scénarios haute résolution et PPP dynamique courants. Découvrez également comment configurer des applications Windows Forms pour la prise en charge de la haute résolution.
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325649"
---
# <a name="high-dpi-support-in-windows-forms"></a>Prise en charge des résolutions élevées en Windows Forms

À partir de la .NET Framework 4,7, Windows Forms comprend des améliorations pour les scénarios haute résolution et PPP dynamique courants. notamment :

- Améliorations de la mise à l’échelle et de la disposition d’un certain nombre de contrôles Windows Forms, tels que le <xref:System.Windows.Forms.MonthCalendar> contrôle et le <xref:System.Windows.Forms.CheckedListBox> contrôle.

- Mise à l’échelle à passage unique.  Dans le .NET Framework 4,6 et les versions antérieures, la mise à l’échelle a été effectuée à travers plusieurs passes, ce qui a entraîné une mise à l’échelle de certains contrôles plus que nécessaire.

- Prise en charge des scénarios PPP dynamiques dans lesquels l’utilisateur modifie la résolution ou le facteur d’échelle après le lancement d’une application Windows Forms.

Dans les versions de la .NET Framework à partir de la .NET Framework 4,7, la prise en charge de la haute résolution améliorée est une fonctionnalité d’abonnement. Vous devez configurer votre application pour en tirer parti.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Configuration de votre application Windows Forms pour la prise en charge de la haute résolution

Les nouvelles fonctionnalités de Windows Forms qui prennent en charge la reconnaissance haute résolution sont uniquement disponibles dans les applications qui ciblent le .NET Framework 4,7 et qui s’exécutent sur des systèmes d’exploitation Windows à partir de Windows 10 Creators Update.

En outre, pour configurer la prise en charge des résolutions élevées dans votre application Windows Forms, vous devez effectuer les opérations suivantes :

- Déclarer la compatibilité avec Windows 10.

  Pour ce faire, ajoutez le code suivant à votre fichier manifeste :

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Activez la prise en face à la résolution par moniteur dans le fichier *app.config* .

  Windows Forms introduit un nouvel [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) élément pour prendre en charge de nouvelles fonctionnalités et personnalisations ajoutées à partir de la .NET Framework 4,7. Pour tirer parti des nouvelles fonctionnalités qui prennent en charge la haute résolution, ajoutez ce qui suit à votre fichier de configuration d’application.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > Dans les versions précédentes de la .NET Framework, vous utilisiez le manifeste pour ajouter la prise en charge des résolutions élevées. Cette approche n’est plus recommandée, car elle remplace les paramètres définis sur le fichier app.config.

- Appelez la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> méthode statique.

  Il doit s’agir du premier appel de méthode dans le point d’entrée de votre application. Par exemple :

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Désactivation des fonctionnalités haute résolution individuelles

La définition `DpiAwareness` de la valeur pour `PerMonitorV2` Active toutes les fonctionnalités de reconnaissance haute résolution prises en charge par les versions .NET Framework à partir de la .NET Framework 4,7. En règle générale, cela convient à la plupart des applications Windows Forms. Toutefois, vous souhaiterez peut-être refuser une ou plusieurs fonctionnalités individuelles. La raison la plus importante pour cela est que votre code d’application existant gère déjà cette fonctionnalité.  Par exemple, si votre application gère la mise à l’échelle automatique, vous souhaiterez peut-être désactiver la fonctionnalité de redimensionnement automatique comme suit :

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Pour obtenir la liste des clés individuelles et leurs valeurs, consultez [Windows Forms ajouter un élément de configuration](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nouveaux événements de modification DPI

À partir de la .NET Framework 4,7, trois nouveaux événements vous permettent de gérer par programmation les modifications PPP dynamiques :

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, qui est déclenché lorsque le paramètre DPI d’un contrôle est modifié par programme après qu’un événement de modification de PPP s’est produit pour son contrôle ou formulaire parent.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, qui est déclenché lorsque le paramètre DPI d’un contrôle est modifié par programme avant qu’un événement de modification DPI pour son contrôle ou formulaire parent s’est produit.
- <xref:System.Windows.Forms.Form.DpiChanged>, qui est déclenché lorsque le paramètre PPP change sur le périphérique d’affichage où le formulaire est actuellement affiché.

## <a name="new-helper-methods-and-properties"></a>Nouvelles méthodes et propriétés d’assistance

La .NET Framework 4,7 ajoute également un certain nombre de nouvelles méthodes et propriétés d’assistance qui fournissent des informations sur la mise à l’échelle DPI et vous permettent d’effectuer une mise à l’échelle PPP. notamment :

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, qui convertit une valeur logique en pixels de périphérique.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, qui met à l’échelle une image bitmap sur les DPI logiques pour un appareil.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, qui retourne la valeur PPP de l’appareil actuel.

## <a name="versioning-considerations"></a>Considérations relatives au contrôle de version

En plus de s’exécuter sur .NET Framework 4,7 et Windows 10 Creators Update, votre application peut également s’exécuter dans un environnement dans lequel elle n’est pas compatible avec les améliorations à haute résolution. Dans ce cas, vous devez développer une solution de secours pour votre application. Vous pouvez effectuer cette opération pour effectuer un [dessin personnalisé](./controls/user-drawn-controls.md) afin de gérer la mise à l’échelle.

Pour ce faire, vous devez également déterminer le système d’exploitation sur lequel votre application s’exécute. Vous pouvez le faire avec du code semblable au suivant :

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Notez que votre application ne détectera pas correctement Windows 10 si elle n’était pas listée en tant que système d’exploitation pris en charge dans le manifeste de l’application.

Vous pouvez également vérifier la version de la .NET Framework à laquelle l’application a été générée :

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Voir aussi

- [Windows Forms ajouter un élément de configuration](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Réglage de la taille et de l’échelle de Windows Forms](adjusting-the-size-and-scale-of-windows-forms.md)
