---
title: 'Atténuation : prise en charge du pointeur tactile et du stylet'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9264d8eb7923663061f9bccfffe5b8f5254549f0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379889"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="21408-102">Atténuation : prise en charge du pointeur tactile et du stylet</span><span class="sxs-lookup"><span data-stu-id="21408-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="21408-103">Les applications WPF qui ciblent .NET Framework 4.7 et sont en cours d’exécution sur des systèmes Windows à compter de la mise à jour Windows 10 Creators Update peuvent activer une pile facultative tactile/de stylet WPF basée sur `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="21408-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="21408-104">Impact</span><span class="sxs-lookup"><span data-stu-id="21408-104">Impact</span></span>

<span data-ttu-id="21408-105">Les développeurs qui n’activent pas explicitement la prise en charge du pointeur tactile/au stylet ne devraient voir aucun changement de comportement tactile/au stylet avec WPF.</span><span class="sxs-lookup"><span data-stu-id="21408-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="21408-106">Voici des problèmes connus avec le paramètre de pile facultative tactile/de stylet basée sur `WM_POINTER` :</span><span class="sxs-lookup"><span data-stu-id="21408-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="21408-107">Pas de prise en charge de l’écriture manuscrite en temps réel.</span><span class="sxs-lookup"><span data-stu-id="21408-107">No support for real-time inking.</span></span>

   <span data-ttu-id="21408-108">Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="21408-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="21408-109">Changements de comportement en raison de modifications dans la promotion d’événements tactiles/de stylet en événements de souris.</span><span class="sxs-lookup"><span data-stu-id="21408-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="21408-110">La manipulation peut se comporter différemment.</span><span class="sxs-lookup"><span data-stu-id="21408-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="21408-111">Le glisser-déplacer ne réagit pas correctement à l’entrée tactile.</span><span class="sxs-lookup"><span data-stu-id="21408-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="21408-112">(Cela n’affecte pas l’entrée du stylet.)</span><span class="sxs-lookup"><span data-stu-id="21408-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="21408-113">Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet.</span><span class="sxs-lookup"><span data-stu-id="21408-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="21408-114">Cela peut éventuellement entraîner une absence de réponse de la part de l’application jusqu’à ce que l’entrée de la souris soit détectée.</span><span class="sxs-lookup"><span data-stu-id="21408-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="21408-115">Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.</span><span class="sxs-lookup"><span data-stu-id="21408-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="21408-116">Si vous activez la prise en charge tactile/du stylet basée sur WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="21408-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="21408-117">Les développeurs qui souhaitent activer cette pile peuvent ajouter les éléments suivants au fichier app.config de l’application :</span><span class="sxs-lookup"><span data-stu-id="21408-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="21408-118">La suppression de cette entrée ou l’affectation de la valeur `false` désactive cette pile facultative.</span><span class="sxs-lookup"><span data-stu-id="21408-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="21408-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21408-119">See also</span></span>

- [<span data-ttu-id="21408-120">Reciblage des modifications dans le .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="21408-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
