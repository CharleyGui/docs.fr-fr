---
title: Compteurs de performance et applications côte à côte in-process
description: Examinez les compteurs de performance et les applications côte à côte in-process dans .NET. Utilisez Perfmon.exe pour différencier les compteurs de performance pour chaque Runtime.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
ms.openlocfilehash: eb05d9f5f930420827c6b3d94ea0ed34f64464fd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803857"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Compteurs de performance et applications côte à côte in-process
À l’aide de l’Analyseur de performances (Perfmon.exe), il est possible de différencier les compteurs de performance pour chaque runtime. Cette rubrique décrit la modification du Registre nécessaire pour activer cette fonctionnalité.  
  
## <a name="the-default-behavior"></a>Comportement par défaut  
 Par défaut, l’Analyseur de performances affiche les compteurs de performance pour chaque application. Toutefois, il existe deux scénarios dans lesquels cela pose problème :  
  
- Quand vous surveillez deux applications qui ont le même nom. Par exemple, si les deux applications se nomment MonApp.exe, l’une sera affichée en tant que **MonApp** et l’autre en tant que **MonApp#1** dans la colonne **Instance**. Dans ce cas, il est difficile de faire correspondre un compteur de performance à une application particulière. On ne sait pas trop si les données recueillies pour **MonApp#1** font référence à la première MonApp.exe ou à la deuxième MonApp.exe.  
  
- Quand une application utilise plusieurs instances du Common Language Runtime. Le .NET Framework 4 prend en charge les scénarios d’hébergement côte à côte in-process. autrement dit, un processus ou une application unique peut charger plusieurs instances du common language runtime. Si une application nommée MonApp.exe charge deux instances d’exécution par défaut, elles sont désignées dans la colonne **Instance** en tant que **MonApp** et **MonApp#1**. Dans ce cas, il est difficile de savoir si **MonApp** et **MonApp#1** font référence à deux applications portant le même nom ou à la même application avec deux runtimes. Si plusieurs applications du même nom chargent plusieurs runtimes, il y a encore plus d’ambiguïté.  
  
 Vous pouvez définir une clé de Registre pour lever cette ambiguïté. Pour les applications développées à l’aide de l' .NET Framework 4, cette modification du Registre ajoute un identificateur de processus suivi d’un identificateur d’instance du Runtime au nom de l’application dans la colonne d' **instance** . Au lieu d’une *application* ou d’une *application*#1, l’application est maintenant identifiée comme *application*_ `p` *ProcessID* \_ `r` *runtimeID* dans la colonne d' **instance** . Si une application a été développée à l’aide d’une version antérieure du Common Language Runtime, cette instance est représentée en tant qu' *application \_ * `p` *ProcessID* , à condition que le .NET Framework 4 soit installé.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Compteurs de performance pour les applications côte à côte in-process  
 Pour gérer les compteurs de performance pour plusieurs versions du Common Language Runtime hébergées dans une application unique, vous devez modifier un paramètre de clé de Registre, comme indiqué dans le tableau suivant.  
  
|||  
|-|-|  
|Nom de clé|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|Nom de la valeur|ProcessNameFormat|  
|Type de valeur|REG_DWORD|  
|Valeur|1 (0x00000001)|  
  
 La valeur 0 pour `ProcessNameFormat` indique que le comportement par défaut est « Activé » ; autrement dit, Perfmon.exe affiche les compteurs de performance pour chaque application. Quand vous affectez la valeur 1, Perfmon.exe lève l’ambiguïté liée aux versions multiples d’une application et fournit des compteurs de performance pour chaque runtime. Toute autre valeur pour le paramètre de clé de Registre `ProcessNameFormat` est non prise en charge et réservée à un usage ultérieur.  
  
 Après avoir mis à jour le paramètre de clé de Registre `ProcessNameFormat`, vous devez redémarrer Perfmon.exe ou tout autre consommateur de compteurs de performance afin que la nouvelle fonctionnalité de nommage d’instance fonctionne correctement.  
  
 L’exemple suivant montre comment modifier la valeur `ProcessNameFormat` par programmation.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Lorsque vous apportez cette modification au registre, Perfmon.exe affiche les noms des applications qui ciblent le .NET Framework 4 As *application*_ `p` *ProcessID* \_ `r` *runtimeID*, où *application* est le nom de l’application, *ProcessID* est l’identificateur de processus de l’application et *runtimeID* est un identificateur de Common Language Runtime. Par exemple, si une application nommée MonApp.exe charge deux instances du Common Language Runtime, Perfmon.exe peut identifier une instance comme MonApp_p1416_r10 et la deuxième comme MonApp_p3160_r10. L’identificateur de runtime lève uniquement l’ambiguïté liée aux runtimes dans un processus ; il ne fournit aucune autre information sur le runtime. (Par exemple, l’ID de runtime n’a aucun lien avec la version ou la référence SKU du runtime.)  
  
 Si le .NET Framework 4 est installé, la modification du Registre affecte également les applications qui ont été développées à l’aide de versions antérieures du .NET Framework. Celles-ci apparaissent dans Perfmon.exe en tant que *application_* `p` *ProcessID*, où *application* est le nom de l’application et *ProcessID* est l’identificateur du processus. Par exemple, si les compteurs de performance de deux applications nommées MonApp.exe sont analysés, l’un d’eux peut apparaître comme MonApp_p23900 et l’autre comme MonApp_p24908.  
  
> [!NOTE]
> L’identificateur de processus élimine l’ambiguïté liée à la résolution de deux applications du même nom qui utilisent des versions antérieures du runtime. Aucun identificateur de runtime n’est nécessaire pour les versions antérieures, car les versions précédentes du Common Language Runtime ne prennent pas en charge les scénarios côte à côte.  
  
 Si la .NET Framework 4 n’est pas présente ou a été désinstallée, la définition de la clé de Registre n’a aucun effet. Cela signifie que deux applications portant le même nom continueront d’apparaître dans Perfmon.exe comme *application* et *application#1* (par exemple, **MonApp** et **MonApp#1**).
