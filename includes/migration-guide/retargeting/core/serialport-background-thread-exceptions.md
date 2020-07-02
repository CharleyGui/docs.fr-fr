---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614502"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="d6458-101">Exceptions de thread d’arrière-plan SerialPort</span><span class="sxs-lookup"><span data-stu-id="d6458-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="d6458-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d6458-102">Details</span></span>

<span data-ttu-id="d6458-103">Les threads d’arrière-plan créés avec des flux <xref:System.IO.Ports.SerialPort> ne terminent plus le processus quand des exceptions de système d’exploitation sont levées.</span><span class="sxs-lookup"><span data-stu-id="d6458-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="d6458-104">Dans les applications qui ciblent .NET Framework 4.7 et les versions antérieures, un processus est terminé quand une exception de système d’exploitation est levée sur un thread d’arrière-plan créé avec un flux <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="d6458-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="d6458-105">Dans les applications qui ciblent .NET Framework 4.7.1 ou une version ultérieure, les threads d’arrière-plan attendent la fin des événements de système d’exploitation liés au port série actif et peuvent planter dans certains cas, comme la suppression soudaine du port série.</span><span class="sxs-lookup"><span data-stu-id="d6458-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6458-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d6458-106">Suggestion</span></span>

<span data-ttu-id="d6458-107">Pour les applications qui ciblent .NET Framework 4.7.1, vous pouvez refuser la gestion des exceptions en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="d6458-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="d6458-108">Pour les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.7.1 ou une version ultérieure, vous pouvez accepter la prise en charge de la gestion des exceptions en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="d6458-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="d6458-109">Nom</span><span class="sxs-lookup"><span data-stu-id="d6458-109">Name</span></span>    | <span data-ttu-id="d6458-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="d6458-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6458-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="d6458-111">Scope</span></span>   | <span data-ttu-id="d6458-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d6458-112">Minor</span></span>       |
| <span data-ttu-id="d6458-113">Version</span><span class="sxs-lookup"><span data-stu-id="d6458-113">Version</span></span> | <span data-ttu-id="d6458-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d6458-114">4.7.1</span></span>       |
| <span data-ttu-id="d6458-115">Type</span><span class="sxs-lookup"><span data-stu-id="d6458-115">Type</span></span>    | <span data-ttu-id="d6458-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d6458-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d6458-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="d6458-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
