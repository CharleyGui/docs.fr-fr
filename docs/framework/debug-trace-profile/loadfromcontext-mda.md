---
title: Assistant Débogage managé loadFromContext
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181805"
---
# <a name="loadfromcontext-mda"></a>Assistant Débogage managé loadFromContext
L’Assistant Débogage managé `loadFromContext` est activé si un assembly est chargé dans le contexte `LoadFrom`. Cette situation peut se produire suite à l’appel <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou d’autres méthodes similaires.  
  
## <a name="symptoms"></a>Symptômes  
 L’utilisation de certaines méthodes de chargeur peut aboutir au chargement des assemblys dans le contexte `LoadFrom`. L’utilisation de ce contexte peut entraîner un comportement inattendu de la sérialisation, des opérations de cast et de la résolution des dépendances. En règle générale, il est recommandé de charger les assemblys dans le contexte `Load` pour éviter ces problèmes. Il est difficile de déterminer le contexte dans lequel un assembly a été chargé sans cet Assistant Débogage managé.  
  
## <a name="cause"></a>Cause :  
 En règle générale, un assembly a été chargé dans le contexte `LoadFrom` s’il a été chargé à partir d’un chemin en dehors du contexte `Load`, comme le Global Assembly Cache ou la propriété <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.  
  
## <a name="resolution"></a>Résolution  
 Configurez les applications pour que les appels de <xref:System.Reflection.Assembly.LoadFrom%2A> ne soient plus nécessaires. Vous pouvez pour cela utiliser les techniques suivantes :  
  
- Installez les assemblys dans le Global Assembly Cache.  
  
- Placez les assemblys dans le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> pour <xref:System.AppDomain>. Dans le cas le domaine par défaut, le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> est celui qui contient le fichier exécutable qui a démarré le processus. Ceci peut également nécessiter la création d’un <xref:System.AppDomain> s’il n’est pas pratique de déplacer l’assembly.  
  
- Ajoutez un chemin de détection au fichier de configuration (.config) de votre application ou aux domaines d’application secondaires si les assemblys dépendants se trouvent dans des répertoires enfants par rapport à l’exécutable.  
  
 Dans chaque cas, le code peut être changé de façon à utiliser la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 L’Assistant Débogage managé n’a pas d’effet sur le CLR. Il indique le contexte qui a été utilisé à la suite d’une demande de chargement.  
  
## <a name="output"></a>Output  
 L’Assistant Débogage managé signale que l’assembly a été chargé dans le contexte `LoadFrom`. Il spécifie le nom simple de l’assembly et le chemin. Il suggère également des mesures de limitation des risques pour éviter d’utiliser le contexte `LoadFrom`.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant illustre une situation qui peut activer cet Assistant Débogage managé :  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
