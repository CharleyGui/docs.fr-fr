---
title: 'Modification avec rupture : les chemins de code UTF-7 sont obsolètes'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les constructeurs UTF7 et UTF7Encoding sont obsolètes.
ms.date: 11/01/2020
ms.openlocfilehash: d58305f59a30cdf31a525c3789bd6497201c50ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760891"
---
# <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="13874-103">Les chemins d’accès de code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="13874-103">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="13874-104">L’encodage UTF-7 n’est plus utilisé dans les applications, et de nombreuses spécifications [interdisent désormais son utilisation](https://security.stackexchange.com/a/68609/3573) dans l’échange.</span><span class="sxs-lookup"><span data-stu-id="13874-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="13874-105">Il est également occasionnellement [utilisé comme vecteur d’attaque dans les](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) applications qui ne prévoient pas la présence de données encodées en UTF-7.</span><span class="sxs-lookup"><span data-stu-id="13874-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="13874-106">Microsoft vous avertit de l’utilisation de <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> car il ne fournit pas de détection d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="13874-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="13874-107">Par conséquent, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="13874-107">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="13874-108">De plus, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> et <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> ne vous autorisent plus à spécifier `UTF-7` .</span><span class="sxs-lookup"><span data-stu-id="13874-108">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

## <a name="change-description"></a><span data-ttu-id="13874-109">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="13874-109">Change description</span></span>

<span data-ttu-id="13874-110">Auparavant, vous pouviez créer une instance de l’encodage UTF-7 à l’aide des <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> API.</span><span class="sxs-lookup"><span data-stu-id="13874-110">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="13874-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="13874-111">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="13874-112">En outre, une instance qui représente l’encodage UTF-7 a été énumérée par la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode, qui énumère toutes les <xref:System.Text.Encoding> instances inscrites sur le système.</span><span class="sxs-lookup"><span data-stu-id="13874-112">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="13874-113">À compter de .NET 5,0, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont obsolètes et produisent des avertissements `SYSLIB0001` (ou `MSLIB0001` dans les versions préliminaires).</span><span class="sxs-lookup"><span data-stu-id="13874-113">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="13874-114">Toutefois, pour réduire le nombre d’avertissements reçus par les appelants lors de l’utilisation de la <xref:System.Text.UTF7Encoding> classe, le <xref:System.Text.UTF7Encoding> type lui-même n’est pas marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="13874-114">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="13874-115">En outre, les <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> méthodes traitent le nom d’encodage `utf-7` et la page de codes `65000` comme `unknown` .</span><span class="sxs-lookup"><span data-stu-id="13874-115">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="13874-116">Le traitement de l’encodage `unknown` entraîne la levée par la méthode d’un <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="13874-116">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="13874-117">Enfin, la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode n’inclut pas l’encodage UTF-7 dans le <xref:System.Text.EncodingInfo> tableau qu’elle retourne.</span><span class="sxs-lookup"><span data-stu-id="13874-117">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="13874-118">L’encodage est exclu, car il ne peut pas être instancié.</span><span class="sxs-lookup"><span data-stu-id="13874-118">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a><span data-ttu-id="13874-119">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="13874-119">Reason for change</span></span>

<span data-ttu-id="13874-120">De nombreuses applications appellent `Encoding.GetEncoding("encoding-name")` avec une valeur de nom d’encodage fournie par une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="13874-120">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="13874-121">Par exemple, un client ou un serveur Web peut prendre la `charset` partie de l' `Content-Type` en-tête et passer directement la valeur à `Encoding.GetEncoding` sans la valider.</span><span class="sxs-lookup"><span data-stu-id="13874-121">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="13874-122">Cela pourrait permettre à un point de terminaison malveillant de spécifier `Content-Type: ...; charset=utf-7` , ce qui pourrait entraîner un comportement Inpossible de l’application de réception.</span><span class="sxs-lookup"><span data-stu-id="13874-122">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="13874-123">En outre, la désactivation des chemins d’accès de code UTF-7 permet d’optimiser les compilateurs, tels que ceux utilisés par éblouissant, pour supprimer entièrement ces chemins de code de l’application résultante.</span><span class="sxs-lookup"><span data-stu-id="13874-123">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="13874-124">Par conséquent, les applications compilées s’exécutent plus efficacement et occupent moins d’espace disque.</span><span class="sxs-lookup"><span data-stu-id="13874-124">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="13874-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="13874-125">Version introduced</span></span>

<span data-ttu-id="13874-126">5.0</span><span class="sxs-lookup"><span data-stu-id="13874-126">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="13874-127">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="13874-127">Recommended action</span></span>

<span data-ttu-id="13874-128">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="13874-128">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="13874-129">Toutefois, pour les applications qui ont précédemment activé les chemins de code relatifs à UTF-7, prenez en compte les instructions qui suivent.</span><span class="sxs-lookup"><span data-stu-id="13874-129">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="13874-130">Si votre application appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> avec des noms d’encodage inconnus fournis par une source non fiable :</span><span class="sxs-lookup"><span data-stu-id="13874-130">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="13874-131">Au lieu de cela, comparez les noms d’encodage à une liste verte configurable.</span><span class="sxs-lookup"><span data-stu-id="13874-131">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="13874-132">La liste verte configurable doit au minimum inclure le « UTF-8 » standard du secteur.</span><span class="sxs-lookup"><span data-stu-id="13874-132">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="13874-133">En fonction de vos clients et des exigences réglementaires, vous devrez peut-être également autoriser les encodages spécifiques à une région, par exemple « GB18030 ».</span><span class="sxs-lookup"><span data-stu-id="13874-133">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="13874-134">Si vous n’implémentez pas de liste verte, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> retourne tout <xref:System.Text.Encoding> ce qui est intégré au système ou qui est inscrit via un personnalisé <xref:System.Text.EncodingProvider> .</span><span class="sxs-lookup"><span data-stu-id="13874-134">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="13874-135">Auditez les exigences de votre service afin de vérifier qu’il s’agit du comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="13874-135">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="13874-136">UTF-7 continue d’être désactivé par défaut, sauf si votre application réactive le commutateur de compatibilité mentionné plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="13874-136">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="13874-137">Si vous utilisez <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dans votre propre protocole ou format de fichier :</span><span class="sxs-lookup"><span data-stu-id="13874-137">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="13874-138">Basculez vers à l’aide de <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="13874-138">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="13874-139">UTF-8 est une norme de l’industrie qui est largement prise en charge dans les langages, les systèmes d’exploitation et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="13874-139">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="13874-140">L’utilisation d’UTF-8 facilite la maintenance à venir de votre code et le rend plus interopérable avec le reste de l’écosystème.</span><span class="sxs-lookup"><span data-stu-id="13874-140">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="13874-141">Si vous comparez une <xref:System.Text.Encoding> instance à <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="13874-141">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="13874-142">Au lieu de cela, envisagez d’effectuer une vérification par rapport à la page de codes UTF-7 connue, qui est `65000` .</span><span class="sxs-lookup"><span data-stu-id="13874-142">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="13874-143">En comparant à la page de codes, vous évitez l’avertissement et vous gérez également certains cas limites, par exemple si quelqu’un a appelé ou sous- `new UTF7Encoding()` classé le type.</span><span class="sxs-lookup"><span data-stu-id="13874-143">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- <span data-ttu-id="13874-144">Si vous devez utiliser <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> :</span><span class="sxs-lookup"><span data-stu-id="13874-144">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="13874-145">Vous pouvez supprimer l' `SYSLIB0001` avertissement dans le code ou dans le fichier *. csproj* de votre projet.</span><span class="sxs-lookup"><span data-stu-id="13874-145">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="13874-146">La suppression `SYSLIB0001` désactive uniquement les <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> avertissements et obsoletion.</span><span class="sxs-lookup"><span data-stu-id="13874-146">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="13874-147">Il ne désactive pas les autres avertissements et ne modifie pas le comportement des API comme <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="13874-147">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="13874-148">Si vous devez prendre en charge `Encoding.GetEncoding("utf-7", ...)` :</span><span class="sxs-lookup"><span data-stu-id="13874-148">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="13874-149">Vous pouvez réactiver la prise en charge de ce à l’aide d’un commutateur de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="13874-149">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="13874-150">Ce commutateur de compatibilité peut être spécifié dans le fichier *. csproj* de l’application ou dans un [fichier de configuration au moment](../../../run-time-config/index.md)de l’exécution, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="13874-150">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="13874-151">Dans le fichier *. csproj* de l’application :</span><span class="sxs-lookup"><span data-stu-id="13874-151">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="13874-152">Dans l'runtimeconfig.template.jsde l’application *sur* le fichier :</span><span class="sxs-lookup"><span data-stu-id="13874-152">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="13874-153">Si vous réactivez la prise en charge d’UTF-7, vous devez effectuer une révision de sécurité du code qui appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="13874-153">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="13874-154">API affectées</span><span class="sxs-lookup"><span data-stu-id="13874-154">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
