---
title: Assistant Débogage managé invalidApartmentStateChange
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
ms.openlocfilehash: 8acafcc2fba9a7d30cc77f25f06adaca7c79db32
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217412"
---
# <a name="invalidapartmentstatechange-mda"></a>Assistant Débogage managé invalidApartmentStateChange
L’Assistant Débogage managé `invalidApartmentStateChange` est activé par l’un des deux problèmes suivants :  
  
- Une tentative est effectuée pour modifier l’état de cloisonnement COM d’un thread qui a déjà été initialisé par COM à un état de cloisonnement différent.  
  
- L’état de cloisonnement COM d’un thread change de manière inopinée.  
  
## <a name="symptoms"></a>Symptômes  
  
- L’état de cloisonnement COM d’un thread ne correspond pas à ce qui a été demandé. Cela peut entraîner l’utilisation de proxies pour des composants COM qui ont un modèle de thread différent du modèle courant. Cela peut également provoquer la levée d’une <xref:System.InvalidCastException> lors de l’appel de l’objet COM via des interfaces qui ne sont pas définies pour le marshaling entre cloisonnements.  
  
- L’état de cloisonnement COM du thread est différent de celui qui est attendu. Cela peut provoquer une <xref:System.Runtime.InteropServices.COMException> avec la valeur HRESULT RPC_E_WRONG_THREAD ainsi qu’une <xref:System.InvalidCastException> quand des appels sont effectués sur un [wrapper RCW (Runtime Callable Wrapper)](../../standard/native-interop/runtime-callable-wrapper.md). Cela peut également conduire plusieurs threads à accéder en même temps à certains composants COM à thread unique, ce qui risque d’entraîner une altération ou une perte de données.  
  
## <a name="cause"></a>Cause :  
  
- Le thread a été précédemment initialisé à un état de cloisonnement COM différent. Notez que l’état de cloisonnement d’un thread peut être défini explicitement ou implicitement. Les opérations explicites incluent la propriété <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> et les méthodes <xref:System.Threading.Thread.SetApartmentState%2A> et <xref:System.Threading.Thread.TrySetApartmentState%2A>. <xref:System.Threading.Thread.Start%2A> est implicitement affecté à un thread créé à l’aide de la méthode <xref:System.Threading.ApartmentState.MTA>, à moins que <xref:System.Threading.Thread.SetApartmentState%2A> ne soit appelé avant le démarrage du thread. De même, la valeur <xref:System.Threading.ApartmentState.MTA> est implicitement affectée au thread principal de l’application, à moins que l’attribut <xref:System.STAThreadAttribute> ne soit spécifié sur la méthode principale.  
  
- La méthode `CoUninitialize` (ou la méthode `CoInitializeEx`) avec un modèle de concurrence différent est appelée sur le thread.  
  
## <a name="resolution"></a>Résolution  
 Définissez l’état de cloisonnement du thread avant que son exécution ne commence ou appliquez l’attribut <xref:System.STAThreadAttribute> ou l’attribut <xref:System.MTAThreadAttribute> à la méthode principale de l’application.  
  
 Dans l’idéal, pour la deuxième cause, le code qui appelle la méthode `CoUninitialize` doit être modifié pour différer l’appel jusqu’à ce que le thread soit sur le point de s’arrêter et qu’aucun des RCW ou de leurs composants COM sous-jacents ne soient encore utilisés par le thread. Toutefois, s’il est impossible de modifier le code qui appelle la méthode `CoUninitialize`, aucun RCW ne doit être utilisé par des threads non initialisés de cette façon.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  
 État de cloisonnement COM du thread actuel et état que le code tentait d’appliquer.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre une situation qui peut activer cet Assistant Débogage managé.  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
