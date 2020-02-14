---
title: Assistant Débogage managé pInvokeStackImbalance
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
ms.openlocfilehash: c789e8cb409bd4c59c91d6b646efe428afe7c86d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217243"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance (MDA)

Le `PInvokeStackImbalance` Assistant Débogage managé (MDA) est activé quand le CLR détecte que la profondeur de la pile après un appel de code non managé ne correspond pas à la profondeur de la pile attendue, étant donné la Convention d’appel spécifiée dans l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> et la déclaration des paramètres dans la signature managée.

L'Assistant Débogage managé (MDA) `PInvokeStackImbalance` est implémenté uniquement pour les plateformes 32 bits x86.

> [!NOTE]
> L’Assistant Débogage managé `PInvokeStackImbalance` est désactivé par défaut. Dans Visual Studio 2017 et versions ultérieures, le MDA `PInvokeStackImbalance` s’affiche dans la liste **Assistants Débogage managé** de la boîte de dialogue **paramètres d’exception** (qui s’affiche lorsque vous sélectionnez **Déboguer** > les **paramètres d’exception** > **Windows** ). Toutefois, si vous activez ou désactivez la case à cocher **arrêter en cas d’exception** , l’Assistant Débogage managé n’est pas activé ou désactivé. il contrôle uniquement si Visual Studio lève une exception lorsque l’Assistant Débogage managé est activé.

## <a name="symptoms"></a>Symptômes

Une application rencontre une violation d'accès ou une altération de la mémoire pendant ou après un appel de code non managé.

## <a name="cause"></a>Cause :

Il se peut que la signature managée de l'appel de code non managé ne corresponde pas à la signature non managée de la méthode qui est appelée.  Cette incompatibilité peut être due au fait que la signature managée ne déclare pas le nombre correct de paramètres ou ne spécifie pas la taille appropriée pour les paramètres.  L’Assistant Débogage managé (MDA) peut également être activé parce que la convention d’appel, éventuellement spécifiée par l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute>, ne correspond pas à la convention d’appel non managée.

## <a name="resolution"></a>Résolution

Vérifiez que la signature managée de l'appel de code non managé et la convention d'appel correspondent à la signature et à la convention d'appel de la cible native.  Essayez de spécifier explicitement la convention d’appel à la fois du côté managé et du côté non managé. Il est également possible, mais moins probable, que la fonction non managée ait déséquilibré la pile pour une raison quelconque, telle qu'un bogue dans le compilateur non managé.

## <a name="effect-on-the-runtime"></a>Effet sur le runtime

Oblige tous les appels de code non managé à prendre le chemin d’accès non optimisé dans le CLR.

## <a name="output"></a>Output

Le message de l'Assistant Débogage managé (MDA) donne le nom de l'appel de méthode d'appel de code non managé qui provoque le déséquilibre de la pile. Voici un exemple de message d'un appel de code non managé sur la méthode `SampleMethod` :

**Un appel à la fonction PInvoke’SampleMethod’a déséquilibré la pile. Cela est probablement dû au fait que la signature PInvoke managée ne correspond pas à la signature cible non managée. Vérifiez que la Convention d’appel et les paramètres de la signature PInvoke correspondent à la signature non managée cible.**

## <a name="configuration"></a>Configuration

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
