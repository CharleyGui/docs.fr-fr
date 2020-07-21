---
title: 'Atténuation : Prise en charge du pointeur tactile et du stylet'
description: Découvrez les effets de l’activation d’une pile tactile tactile/de stylet WPF facultative pour les applications WPF qui ciblent .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475422"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="3cb77-103">Atténuation : Prise en charge du pointeur tactile et du stylet</span><span class="sxs-lookup"><span data-stu-id="3cb77-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="3cb77-104">Les applications WPF qui ciblent le .NET Framework 4,7 et s’exécutent sur Windows à partir de Windows 10 Creators Update peuvent activer une `WM_POINTER` pile tactile/de stylet WPF basée sur des facultatifs.</span><span class="sxs-lookup"><span data-stu-id="3cb77-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="3cb77-105">Impact</span><span class="sxs-lookup"><span data-stu-id="3cb77-105">Impact</span></span>

<span data-ttu-id="3cb77-106">Les développeurs qui n’activent pas explicitement la prise en charge du pointeur tactile/au stylet ne devraient voir aucun changement de comportement tactile/au stylet avec WPF.</span><span class="sxs-lookup"><span data-stu-id="3cb77-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="3cb77-107">Voici des problèmes connus avec le paramètre de pile facultative tactile/de stylet basée sur `WM_POINTER` :</span><span class="sxs-lookup"><span data-stu-id="3cb77-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="3cb77-108">Pas de prise en charge de l’écriture manuscrite en temps réel.</span><span class="sxs-lookup"><span data-stu-id="3cb77-108">No support for real-time inking.</span></span>

   <span data-ttu-id="3cb77-109">Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="3cb77-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="3cb77-110">Changements de comportement en raison de modifications dans la promotion d’événements tactiles/de stylet en événements de souris.</span><span class="sxs-lookup"><span data-stu-id="3cb77-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="3cb77-111">La manipulation peut se comporter différemment.</span><span class="sxs-lookup"><span data-stu-id="3cb77-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="3cb77-112">Le glisser-déplacer ne réagit pas correctement à l’entrée tactile.</span><span class="sxs-lookup"><span data-stu-id="3cb77-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="3cb77-113">(Cela n’affecte pas l’entrée du stylet.)</span><span class="sxs-lookup"><span data-stu-id="3cb77-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="3cb77-114">Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet.</span><span class="sxs-lookup"><span data-stu-id="3cb77-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="3cb77-115">Cela peut éventuellement entraîner une absence de réponse de la part de l’application jusqu’à ce que l’entrée de la souris soit détectée.</span><span class="sxs-lookup"><span data-stu-id="3cb77-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="3cb77-116">Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.</span><span class="sxs-lookup"><span data-stu-id="3cb77-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="3cb77-117">Si vous activez la prise en charge tactile/du stylet basée sur WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="3cb77-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="3cb77-118">Les développeurs qui souhaitent activer cette pile peuvent ajouter les éléments suivants au fichier *app.config* de l’application.</span><span class="sxs-lookup"><span data-stu-id="3cb77-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="3cb77-119">La suppression de cette entrée ou l’affectation de la valeur `false` désactive cette pile facultative.</span><span class="sxs-lookup"><span data-stu-id="3cb77-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cb77-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cb77-120">See also</span></span>

- [<span data-ttu-id="3cb77-121">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="3cb77-121">Application compatibility</span></span>](application-compatibility.md)
