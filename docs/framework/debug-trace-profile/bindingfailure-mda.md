---
title: Assistant Débogage managé bindingFailure
description: En savoir plus sur l’Assistant Débogage managé (MDA) bindingFailure, qui est activé lorsqu’un assembly ne parvient pas à se charger dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415626"
---
# <a name="bindingfailure-mda"></a>Assistant Débogage managé bindingFailure

L’Assistant débogage managé (MDA) `bindingFailure` est activé quand le chargement d’un assembly échoue.

## <a name="symptoms"></a>Symptômes

Le code a tenté de charger un assembly à l’aide d’une référence statique ou de l’une des méthodes de chargeur, telles que <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. L’assembly n’est pas chargé et une exception <xref:System.IO.FileNotFoundException> ou <xref:System.IO.FileLoadException> est levée.

## <a name="cause"></a>Cause

Un échec de liaison se produit quand le runtime ne peut pas charger un assembly. Un échec de liaison peut être dû à l’une des situations suivantes :

- Le Common Language Runtime (CLR) ne trouve pas l’assembly demandé. Cela peut se produire par exemple si l’assembly n’est pas installé ou si l’application n’est pas configurée correctement pour trouver l’assembly.

- Un scénario à problème courant est le passage d’un type à un autre domaine d’application. Dans ce cas, le CLR doit charger l’assembly contenant ce type dans l’autre domaine d’application. Il est possible que le runtime ne puisse pas charger l’assembly si l’autre domaine d’application est configuré différemment du domaine d’application d’origine. Les deux domaines d’application peuvent par exemple avoir différentes valeurs de propriété <xref:System.AppDomain.BaseDirectory%2A>.

- L’assembly demandé est endommagé ou n’est pas un assembly.

- Le code qui tente de charger l’assembly ne dispose pas des autorisations de sécurité d’accès du code correctes pour charger des assemblys.

- Les informations d’identification de l’utilisateur ne fournissent pas les autorisations requises pour lire le fichier.

## <a name="resolution"></a>Résolution

La première étape consiste à déterminer pourquoi le CLR n’a pas pu établir de liaison avec l’assembly demandé. Il existe de nombreuses raisons pour lesquelles le runtime est susceptible de ne pas avoir trouvé ou chargé l’assembly demandé, parmi lesquelles les scénarios répertoriés dans la section Cause. Nous vous recommandons d’effectuer les actions suivantes pour éliminer la cause de l’échec de liaison :

- Déterminez la cause à l’aide des données fournies par l’Assistant Débogage managé `bindingFailure` :

  - Exécutez [Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour lire les journaux d’erreur produits par le binder d’assembly.

  - Déterminez si l’assembly se trouve à l’emplacement demandé. Avec les méthodes <xref:System.Reflection.Assembly.LoadFrom%2A> et <xref:System.Reflection.Assembly.LoadFile%2A>, il est facile de déterminer l’emplacement demandé. Avec la méthode <xref:System.Reflection.Assembly.Load%2A>, qui établit une liaison à l’aide de l’identité d’assembly, vous devez rechercher les assemblys qui correspondent à cette identité dans le chemin de sonde de propriété <xref:System.AppDomain.BaseDirectory%2A> du domaine d’application et le global assembly cache.

- Résolvez le problème en fonction de la détermination précédente. Les options de résolution possibles sont les suivantes :

  - Installez l’assembly demandé dans le global assembly cache et appelez la méthode <xref:System.Reflection.Assembly.Load%2A> pour charger l’assembly par identité.

  - Copiez l’assembly demandé dans le répertoire de l’application et appelez la méthode <xref:System.Reflection.Assembly.Load%2A> pour charger l’assembly par identité.

  - Reconfigurez le domaine d’application dans lequel l’échec de liaison s’est produit pour inclure le chemin d’assembly en modifiant la propriété <xref:System.AppDomain.BaseDirectory%2A> ou en ajoutant des chemins de sonde privés.

  - Modifiez la liste de contrôle d’accès pour le fichier afin de permettre à l’utilisateur connecté de lire le fichier.

## <a name="effect-on-the-runtime"></a>Effet sur le runtime

Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il signale uniquement des données relatives aux échecs de liaison.

## <a name="output"></a>Output

L’Assistant Débogage managé signale l’assembly dont le chargement a échoué, notamment le chemin demandé et/ou le nom complet, le contexte de liaison, le domaine d’application dans lequel le chargement a été demandé et la raison de l’échec.

Le nom complet ou le chemin demandé peut être vide si ces données n’étaient pas accessibles au CLR. Si l’appel qui a échoué était un appel à la méthode <xref:System.Reflection.Assembly.Load%2A>, il est probable que le runtime n’a pas pu déterminer le nom complet de l’assembly.

## <a name="configuration"></a>Configuration

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Exemple

L’exemple de code suivant illustre une situation qui peut activer cet Assistant Débogage managé :

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
