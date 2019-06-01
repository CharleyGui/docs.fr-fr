---
title: Compteurs de performance et applications côte à côte in-process
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3f9c9c61afd4c231846adffc4b304a01d59281
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457256"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Compteurs de performance et applications côte à côte in-process
À l’aide de l’Analyseur de performances (Perfmon.exe), il est possible de différencier les compteurs de performance pour chaque runtime. Cette rubrique décrit la modification du Registre nécessaire pour activer cette fonctionnalité.  
  
## <a name="the-default-behavior"></a>Comportement par défaut  
 Par défaut, l’Analyseur de performances affiche les compteurs de performance pour chaque application. Toutefois, il existe deux scénarios dans lesquels cela pose problème :  
  
- Quand vous surveillez deux applications qui ont le même nom. Par exemple, si les deux applications se nomment MonApp.exe, l’une sera affichée en tant que **MonApp** et l’autre en tant que **MonApp#1** dans la colonne **Instance**. Dans ce cas, il est difficile de faire correspondre un compteur de performance à une application particulière. On ne sait pas trop si les données recueillies pour **MonApp#1** font référence à la première MonApp.exe ou à la deuxième MonApp.exe.  
  
- Quand une application utilise plusieurs instances du Common Language Runtime. Le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] prend en charge les scénarios d’hébergement côte à côte in-process ; autrement dit, un même processus ou une même application peut charger plusieurs instances du Common Language Runtime. Si une application nommée MonApp.exe charge deux instances d’exécution par défaut, elles sont désignées dans la colonne **Instance** en tant que **MonApp** et **MonApp#1**. Dans ce cas, il est difficile de savoir si **MonApp** et **MonApp#1** font référence à deux applications portant le même nom ou à la même application avec deux runtimes. Si plusieurs applications du même nom chargent plusieurs runtimes, il y a encore plus d’ambiguïté.  
  
 Vous pouvez définir une clé de Registre pour lever cette ambiguïté. Pour les applications développées à l’aide de .NET Framework 4, cette modification du Registre ajoute un identificateur de processus suivi d’un identificateur d’instance de runtime pour le nom de l’application dans le **Instance** colonne. Au lieu de *application* ou *application*#1, l’application est maintenant identifiée comme *application*_`p`*ID_processus* \_ `r` *ID_runtime* dans la colonne **Instance**. Si une application a été développée à l’aide d’une version précédente du common language runtime, cette instance est représentée en tant que *application\_* `p`*processID* autant que le. NET Framework 4 est installé.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Compteurs de performance pour les applications côte à côte in-process  
 Pour gérer les compteurs de performance pour plusieurs versions du Common Language Runtime hébergées dans une application unique, vous devez modifier un paramètre de clé de Registre, comme indiqué dans le tableau suivant.  
  
|||  
|-|-|  
|Nom de la clé|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|Nom de la valeur|ProcessNameFormat|  
|Type de valeur|REG_DWORD|  
|Value|1 (0x00000001)|  
  
 La valeur 0 pour `ProcessNameFormat` indique que le comportement par défaut est « Activé » ; autrement dit, Perfmon.exe affiche les compteurs de performance pour chaque application. Quand vous affectez la valeur 1, Perfmon.exe lève l’ambiguïté liée aux versions multiples d’une application et fournit des compteurs de performance pour chaque runtime. Toute autre valeur pour le paramètre de clé de Registre `ProcessNameFormat` est non prise en charge et réservée à un usage ultérieur.  
  
 Après avoir mis à jour le paramètre de clé de Registre `ProcessNameFormat`, vous devez redémarrer Perfmon.exe ou tout autre consommateur de compteurs de performance afin que la nouvelle fonctionnalité de nommage d’instance fonctionne correctement.  
  
 L’exemple suivant montre comment modifier la valeur `ProcessNameFormat` par programmation.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Lorsque vous modifiez ce Registre, Perfmon.exe affiche les noms des applications qui ciblent le .NET Framework 4 en tant que *application*_`p`*processID* \_ `r` *Id_runtime*, où *application* est le nom de l’application, *processID* est l’identificateur de processus de l’application, et  *Id_runtime* est un identificateur du common language runtime. Par exemple, si une application nommée MonApp.exe charge deux instances du Common Language Runtime, Perfmon.exe peut identifier une instance comme MonApp_p1416_r10 et la deuxième comme MonApp_p3160_r10. L’identificateur de runtime lève uniquement l’ambiguïté liée aux runtimes dans un processus ; il ne fournit aucune autre information sur le runtime. (Par exemple, l’ID de runtime n’a aucun lien avec la version ou la référence SKU du runtime.)  
  
 Si le .NET Framework 4 est installé, la modification du Registre affecte également les applications développées à l’aide de versions antérieures du .NET Framework. Celles-ci apparaissent dans Perfmon.exe au format *application_* `p`*ID_processus*, où *application* est le nom de l’application et *ID_processus* est l’identificateur de processus. Par exemple, si les compteurs de performance de deux applications nommées MonApp.exe sont analysés, l’un d’eux peut apparaître comme MonApp_p23900 et l’autre comme MonApp_p24908.  
  
> [!NOTE]
>  L’identificateur de processus élimine l’ambiguïté liée à la résolution de deux applications du même nom qui utilisent des versions antérieures du runtime. Aucun identificateur de runtime n’est nécessaire pour les versions antérieures, car les versions précédentes du Common Language Runtime ne prennent pas en charge les scénarios côte à côte.  
  
 Si le .NET Framework 4 n’est pas présent ou a été désinstallé, définition de la clé de Registre n’a aucun effet. Cela signifie que deux applications portant le même nom continueront d’apparaître dans Perfmon.exe comme *application* et *application#1* (par exemple, **MonApp** et **MonApp#1**).
