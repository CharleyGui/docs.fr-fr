---
ms.openlocfilehash: c5204e8c80cb737338b053c39083c0cc43786447
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517324"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="5f44f-101">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f44f-101">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="5f44f-102">`Serialize`les `Deserialize` méthodes et sur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , <xref:System.Runtime.Serialization.Formatter> et <xref:System.Runtime.Serialization.IFormatter> sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="5f44f-102">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete.</span></span> <span data-ttu-id="5f44f-103">En outre, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est interdite par défaut pour les applications ASP.net.</span><span class="sxs-lookup"><span data-stu-id="5f44f-103">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5f44f-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="5f44f-104">Change description</span></span>

<span data-ttu-id="5f44f-105">En raison de [failles de sécurité](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) dans <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , les méthodes suivantes sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="5f44f-105">Due to [security vulnerabilities](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete.</span></span> <span data-ttu-id="5f44f-106">En outre, dans les applications ASP.NET 5,0 et versions ultérieures, elles lèvent un <xref:System.NotSupportedException> , sauf si l’application Web a réactivé la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="5f44f-106">Additionally, in ASP.NET 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="5f44f-107">Ces méthodes sont marquées comme obsolètes dans le cadre d’un effort visant à réduire l’utilisation de au <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sein de l’écosystème .net.</span><span class="sxs-lookup"><span data-stu-id="5f44f-107">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

<span data-ttu-id="5f44f-108">Les méthodes de sérialisation suivantes sont également obsolètes, mais n’ont pas de changements de comportement :</span><span class="sxs-lookup"><span data-stu-id="5f44f-108">The following serialization methods are also now obsolete, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a><span data-ttu-id="5f44f-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5f44f-109">Version introduced</span></span>

<span data-ttu-id="5f44f-110">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="5f44f-110">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5f44f-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5f44f-111">Recommended action</span></span>

- <span data-ttu-id="5f44f-112">Arrêtez l’utilisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> de dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5f44f-112">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="5f44f-113">Au lieu de cela, envisagez d’utiliser <xref:System.Text.Json.JsonSerializer> ou <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="5f44f-113">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="5f44f-114">Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="5f44f-114">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="5f44f-115">Vous pouvez supprimer temporairement l' <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> avertissement au moment de la compilation, qui est `SYSLIB0011` .</span><span class="sxs-lookup"><span data-stu-id="5f44f-115">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="5f44f-116">Nous vous recommandons d’évaluer minutieusement votre code pour déterminer les risques avant de choisir cette option.</span><span class="sxs-lookup"><span data-stu-id="5f44f-116">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="5f44f-117">Le moyen le plus simple de supprimer les avertissements est d’entourer le site d’appel individuel à l’aide de `#pragma` directives.</span><span class="sxs-lookup"><span data-stu-id="5f44f-117">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="5f44f-118">Vous pouvez également supprimer l’avertissement dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5f44f-118">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="5f44f-119">Si vous supprimez l’avertissement dans le fichier projet, l’avertissement est supprimé pour tous les fichiers de code du projet.</span><span class="sxs-lookup"><span data-stu-id="5f44f-119">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="5f44f-120">La suppression de SYSLIB0011 ne supprime pas les avertissements causés par l’utilisation d’autres API obsolètes.</span><span class="sxs-lookup"><span data-stu-id="5f44f-120">Suppressing SYSLIB0011 does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="5f44f-121">Pour continuer à utiliser <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dans les applications ASP.net, vous pouvez la réactiver dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5f44f-121">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="5f44f-122">Toutefois, il est vivement recommandé de ne pas le faire.</span><span class="sxs-lookup"><span data-stu-id="5f44f-122">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="5f44f-123">Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="5f44f-123">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="5f44f-124">Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="5f44f-124">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

#### <a name="category"></a><span data-ttu-id="5f44f-125">Category</span><span class="sxs-lookup"><span data-stu-id="5f44f-125">Category</span></span>

- <span data-ttu-id="5f44f-126">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f44f-126">Core .NET libraries</span></span>
- <span data-ttu-id="5f44f-127">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f44f-127">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f44f-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="5f44f-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
