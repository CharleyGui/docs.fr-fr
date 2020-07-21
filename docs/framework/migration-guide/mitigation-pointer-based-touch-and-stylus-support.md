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
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Atténuation : Prise en charge du pointeur tactile et du stylet

Les applications WPF qui ciblent le .NET Framework 4,7 et s’exécutent sur Windows à partir de Windows 10 Creators Update peuvent activer une `WM_POINTER` pile tactile/de stylet WPF basée sur des facultatifs.

## <a name="impact"></a>Impact

Les développeurs qui n’activent pas explicitement la prise en charge du pointeur tactile/au stylet ne devraient voir aucun changement de comportement tactile/au stylet avec WPF.

Voici des problèmes connus avec le paramètre de pile facultative tactile/de stylet basée sur `WM_POINTER` :

- Pas de prise en charge de l’écriture manuscrite en temps réel.

   Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.

- Changements de comportement en raison de modifications dans la promotion d’événements tactiles/de stylet en événements de souris.

  - La manipulation peut se comporter différemment.

  - Le glisser-déplacer ne réagit pas correctement à l’entrée tactile. (Cela n’affecte pas l’entrée du stylet.)

  - Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet.

      Cela peut éventuellement entraîner une absence de réponse de la part de l’application jusqu’à ce que l’entrée de la souris soit détectée. Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Si vous activez la prise en charge tactile/du stylet basée sur WM_POINTER

Les développeurs qui souhaitent activer cette pile peuvent ajouter les éléments suivants au fichier *app.config* de l’application.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

La suppression de cette entrée ou l’affectation de la valeur `false` désactive cette pile facultative.

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
