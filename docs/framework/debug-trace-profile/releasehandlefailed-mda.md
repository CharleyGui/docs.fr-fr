---
title: releaseHandleFailed (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
ms.openlocfilehash: 265344cb100a41cde5443cd0914dc66271aabf93
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216114"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed (MDA)
L'Assistant Débogage managé (MDA) `releaseHandleFailed` est activé pour avertir les développeurs que la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> d'une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> ou de <xref:System.Runtime.InteropServices.CriticalHandle> retourne la valeur `false`.  
  
## <a name="symptoms"></a>Symptômes  
 Fuites de ressources ou de mémoire.  Si la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> de la classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> ou de <xref:System.Runtime.InteropServices.CriticalHandle> échoue, il est possible que la ressource encapsulée par la classe n'ait pas pu être libérée ou nettoyée.  
  
## <a name="cause"></a>Cause :  
 Les utilisateurs doivent fournir l'implémentation de la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> s'ils créent des classes qui dérivent de <xref:System.Runtime.InteropServices.SafeHandle> ou de <xref:System.Runtime.InteropServices.CriticalHandle>. Les circonstances sont donc spécifiques à chaque ressource. Toutefois, il existe certaines exigences :  
  
- Les types <xref:System.Runtime.InteropServices.SafeHandle> et <xref:System.Runtime.InteropServices.CriticalHandle> représentent des wrappers autour de ressources de processus essentielles. Une fuite de mémoire finirait par rendre le processus inutilisable.  
  
- La méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ne doit pas échouer dans l'exécution de sa fonction. Une ressource acquise par le processus ne peut être libérée qu’avec la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>. C'est pourquoi un échec de la méthode entraîne une fuite de ressource.  
  
- Un échec survenant pendant l’exécution de la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> empêche la libération de la ressource, et constitue un bogue dans l’implémentation de la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> elle-même. C'est au programmeur qu'il revient de s'assurer que le contrat est respecté, même si ce code appelle du code créé par un autre utilisateur pour exécuter sa fonction.  
  
## <a name="resolution"></a>Résolution  
 Passez en revue le code utilisant le type <xref:System.Runtime.InteropServices.SafeHandle> (ou <xref:System.Runtime.InteropServices.CriticalHandle>) spécifique qui a déclenché la notification de l’Assistant Débogage managé et recherchez les endroits où la valeur du handle brut est extraite de <xref:System.Runtime.InteropServices.SafeHandle> et copiée ailleurs. C'est la cause de la plupart des échecs dans les implémentations de <xref:System.Runtime.InteropServices.SafeHandle> ou de <xref:System.Runtime.InteropServices.CriticalHandle>, car le runtime n'effectue plus de suivi de l'utilisation de la valeur du handle brut. Si la copie du handle brut est fermée par la suite, cela peut provoquer l'échec d'un appel ultérieur à <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, car c'est le même handle, désormais non valide, qui fait l'objet d'une tentative de fermeture.  
  
 Une duplication de handle incorrecte peut se produire dans plusieurs cas :  
  
- Recherchez d'éventuels appels à la méthode <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A>. Les appels à cette méthode doivent être extrêmement rares et, s'il y en a, ils doivent être entourés d'appels aux méthodes <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> et <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>. Ces dernières spécifient la partie du code où la valeur du handle brut peut être utilisée en toute sécurité. En dehors de cette partie, ou si le nombre de références n'est jamais incrémenté initialement, la valeur du handle peut être invalidée à tout moment par un appel à <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> ou <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> sur un autre thread. Dès que toutes les utilisations de <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> ont été localisées, vous devez suivre le chemin d’accès emprunté par le handle brut pour vous assurer qu’il n’est pas remis à un composant quelconque qui finira par appeler `CloseHandle` ou une autre méthode native de niveau inférieur qui libérera le handle.  
  
- Assurez-vous que le code utilisé pour initialiser <xref:System.Runtime.InteropServices.SafeHandle> avec une valeur de handle brut valide est propriétaire du handle. Si vous formez <xref:System.Runtime.InteropServices.SafeHandle> autour d'un handle non détenu par votre code sans affecter au paramètre `ownsHandle` la valeur `false` dans le constructeur de base, alors <xref:System.Runtime.InteropServices.SafeHandle> et le véritable propriétaire du handle peuvent tenter de fermer le handle, ce qui se traduit par une erreur dans <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> si <xref:System.Runtime.InteropServices.SafeHandle> n'y accède pas en premier.  
  
- Si <xref:System.Runtime.InteropServices.SafeHandle> est marshalé entre des domaines d’application, vérifiez si la dérivation de <xref:System.Runtime.InteropServices.SafeHandle> utilisée a été marquée comme étant sérialisable. Dans les rares cas où une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> est devenue sérialisable, elle doit implémenter l’interface <xref:System.Runtime.Serialization.ISerializable> ou utiliser l’une des autres techniques permettant de contrôler manuellement le processus de sérialisation et de désérialisation. C'est indispensable dans la mesure où l'action de sérialisation par défaut consiste à créer un clone de bits de la valeur du handle brut incluse et se traduit donc par la présence de deux instances de <xref:System.Runtime.InteropServices.SafeHandle> qui se considèrent toutes deux propriétaires du même handle. Ces deux instances tenteront d'appeler <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sur le même handle à un moment donné. Le deuxième <xref:System.Runtime.InteropServices.SafeHandle> à le faire échouera. Quand vous sérialisez <xref:System.Runtime.InteropServices.SafeHandle>, la solution appropriée consiste à appeler la fonction `DuplicateHandle` ou une fonction similaire pour votre type de handle natif pour effectuer une copie de handle légale distincte. Si votre type de handle ne prend pas en charge cette opération, le type <xref:System.Runtime.InteropServices.SafeHandle> qui l'encapsule ne peut pas devenir sérialisable.  
  
- Il est parfois possible d’identifier la partie où un handle est fermé de façon anticipée (ce qui se traduit par un échec quand la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> est finalement appelée). Pour cela, vous devez placer un point d’arrêt de débogueur sur la routine native utilisée pour libérer le handle, par exemple la fonction `CloseHandle`. Ce n'est pas toujours possible dans les scénarios de tests de contraintes, voire dans les tests fonctionnels de taille moyenne, en raison du trafic important généralement associé à de telles routines. Il peut être utile d’instrumenter le code qui appelle la méthode de libération native, afin de capturer l’identité de l’appelant, ou éventuellement une trace de la pile complète, ainsi que la valeur du handle libéré.  La valeur du handle peut être comparée à la valeur transmise par cet Assistant Débogage managé.  
  
- Notez que certains types de handle natifs, et notamment tous les handles Win32 qui peuvent être libérés via la fonction `CloseHandle`, partagent le même espace de noms de handles. Une mise en production incorrecte d’un type de handle peut provoquer des problèmes avec un autre. Par exemple, fermer accidentellement deux fois un handle d'événement Win32 peut provoquer la fermeture prématurée d'un handle de fichier apparemment non lié. Cela se produit quand le handle est libéré et que la valeur du handle redevient disponible pour le suivi d’une autre ressource, parfois d’un autre type. Si cette libération est suivie d'une deuxième libération erronée, le handle d'un thread non lié risque d'être invalidé.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  
 Message indiquant qu’un <xref:System.Runtime.InteropServices.SafeHandle> ou un <xref:System.Runtime.InteropServices.CriticalHandle> n’a pas réussi à libérer correctement le handle. Par exemple :  
  
```output
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'   
failed to properly release the handle with value 0x0000BEEF. This   
usually indicates that the handle was released incorrectly via   
another means (such as extracting the handle using DangerousGetHandle   
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant peut activer l'Assistant Débogage managé `releaseHandleFailed`.  
  
```csharp
bool ReleaseHandle()  
{  
    // Calling the Win32 CloseHandle function to release the   
    // native handle wrapped by this SafeHandle. This method returns   
    // false on failure, but should only fail if the input is invalid   
    // (which should not happen here). The method specifically must not   
    // fail simply because of lack of resources or other transient   
    // failures beyond the user’s control. That would make it unacceptable   
    // to call CloseHandle as part of the implementation of this method.  
    return CloseHandle(handle);  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
