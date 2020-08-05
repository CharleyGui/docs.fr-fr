---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455755"
---
### <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="fcaaa-101">Les chemins d’accès de code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="fcaaa-101">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="fcaaa-102">L’encodage UTF-7 n’est plus utilisé dans les applications, et de nombreuses spécifications [interdisent désormais son utilisation](https://security.stackexchange.com/a/68609/3573) dans l’échange.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-102">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="fcaaa-103">Il est également occasionnellement [utilisé comme vecteur d’attaque dans les](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) applications qui ne prévoient pas la présence de données encodées en UTF-7.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-103">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="fcaaa-104">Microsoft vous avertit de l’utilisation de <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> car il ne fournit pas de détection d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-104">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="fcaaa-105">Par conséquent, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont désormais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-105">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="fcaaa-106">De plus, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> et <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> ne vous autorisent plus à spécifier `UTF-7` .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-106">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fcaaa-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fcaaa-107">Change description</span></span>

<span data-ttu-id="fcaaa-108">Auparavant, vous pouviez créer une instance de l’encodage UTF-7 à l’aide des <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> API.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-108">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="fcaaa-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-109">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="fcaaa-110">En outre, une instance qui représente l’encodage UTF-7 a été énumérée par la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode, qui énumère toutes les <xref:System.Text.Encoding> instances inscrites sur le système.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-110">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="fcaaa-111">À compter de .NET 5,0, la <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriété et les <xref:System.Text.UTF7Encoding.%23ctor%2A> constructeurs sont obsolètes et produisent des avertissements `SYSLIB0001` (ou `MSLIB0001` dans les versions préliminaires).</span><span class="sxs-lookup"><span data-stu-id="fcaaa-111">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="fcaaa-112">Toutefois, pour réduire le nombre d’avertissements reçus par les appelants lors de l’utilisation de la <xref:System.Text.UTF7Encoding> classe, le <xref:System.Text.UTF7Encoding> type lui-même n’est pas marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-112">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="fcaaa-113">En outre, les <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> méthodes traitent le nom d’encodage `utf-7` et la page de codes `65000` comme `unknown` .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-113">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="fcaaa-114">Le traitement de l’encodage `unknown` entraîne la levée par la méthode d’un <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-114">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="fcaaa-115">Enfin, la <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> méthode n’inclut pas l’encodage UTF-7 dans le <xref:System.Text.EncodingInfo> tableau qu’elle retourne.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-115">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="fcaaa-116">L’encodage est exclu, car il ne peut pas être instancié.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-116">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a><span data-ttu-id="fcaaa-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="fcaaa-117">Reason for change</span></span>

<span data-ttu-id="fcaaa-118">De nombreuses applications appellent `Encoding.GetEncoding("encoding-name")` avec une valeur de nom d’encodage fournie par une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-118">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="fcaaa-119">Par exemple, un client ou un serveur Web peut prendre la `charset` partie de l' `Content-Type` en-tête et passer directement la valeur à `Encoding.GetEncoding` sans la valider.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-119">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="fcaaa-120">Cela pourrait permettre à un point de terminaison malveillant de spécifier `Content-Type: ...; charset=utf-7` , ce qui pourrait entraîner un comportement Inpossible de l’application de réception.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-120">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="fcaaa-121">En outre, la désactivation des chemins d’accès de code UTF-7 permet d’optimiser les compilateurs, tels que ceux utilisés par éblouissant, pour supprimer entièrement ces chemins de code de l’application résultante.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-121">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="fcaaa-122">Par conséquent, les applications compilées s’exécutent plus efficacement et occupent moins d’espace disque.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-122">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fcaaa-123">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fcaaa-123">Version introduced</span></span>

<span data-ttu-id="fcaaa-124">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="fcaaa-124">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fcaaa-125">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fcaaa-125">Recommended action</span></span>

<span data-ttu-id="fcaaa-126">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-126">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="fcaaa-127">Toutefois, pour les applications qui ont précédemment activé les chemins de code relatifs à UTF-7, prenez en compte les instructions qui suivent.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-127">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="fcaaa-128">Si votre application appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> avec des noms d’encodage inconnus fournis par une source non fiable :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-128">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="fcaaa-129">Au lieu de cela, comparez les noms d’encodage à une liste verte configurable.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-129">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="fcaaa-130">La liste verte configurable doit au minimum inclure le « UTF-8 » standard du secteur.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-130">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="fcaaa-131">En fonction de vos clients et des exigences réglementaires, vous devrez peut-être également autoriser les encodages spécifiques à une région, par exemple « GB18030 ».</span><span class="sxs-lookup"><span data-stu-id="fcaaa-131">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="fcaaa-132">Si vous n’implémentez pas de liste verte, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> retourne tout <xref:System.Text.Encoding> ce qui est intégré au système ou qui est inscrit via un personnalisé <xref:System.Text.EncodingProvider> .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-132">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="fcaaa-133">Auditez les exigences de votre service afin de vérifier qu’il s’agit du comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-133">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="fcaaa-134">UTF-7 continue d’être désactivé par défaut, sauf si votre application réactive le commutateur de compatibilité mentionné plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-134">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="fcaaa-135">Si vous utilisez <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dans votre propre protocole ou format de fichier :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-135">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="fcaaa-136">Basculez vers à l’aide de <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-136">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="fcaaa-137">UTF-8 est une norme de l’industrie qui est largement prise en charge dans les langages, les systèmes d’exploitation et les runtimes.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-137">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="fcaaa-138">L’utilisation d’UTF-8 facilite la maintenance à venir de votre code et le rend plus interopérable avec le reste de l’écosystème.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-138">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="fcaaa-139">Si vous comparez une <xref:System.Text.Encoding> instance à <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-139">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="fcaaa-140">Au lieu de cela, envisagez d’effectuer une vérification par rapport à la page de codes UTF-7 connue, qui est `65000` .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-140">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="fcaaa-141">En comparant à la page de codes, vous évitez l’avertissement et vous gérez également certains cas limites, par exemple si quelqu’un a appelé ou sous- `new UTF7Encoding()` classé le type.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-141">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="fcaaa-142">Si vous devez utiliser <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-142">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="fcaaa-143">Vous pouvez supprimer l' `SYSLIB0001` avertissement dans le code ou dans le fichier *. csproj* de votre projet.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-143">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

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
  > <span data-ttu-id="fcaaa-144">La suppression `SYSLIB0001` désactive uniquement les <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> avertissements et obsoletion.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-144">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="fcaaa-145">Il ne désactive pas les autres avertissements et ne modifie pas le comportement des API comme <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-145">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="fcaaa-146">Si vous devez prendre en charge `Encoding.GetEncoding("utf-7", ...)` :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-146">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="fcaaa-147">Vous pouvez réactiver la prise en charge de ce à l’aide d’un commutateur de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-147">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="fcaaa-148">Ce commutateur de compatibilité peut être spécifié dans le fichier *. csproj* de l’application ou dans un [fichier de configuration au moment](../../../../docs/core/run-time-config/index.md)de l’exécution, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="fcaaa-148">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../../docs/core/run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="fcaaa-149">Dans le fichier *. csproj* de l’application :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-149">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="fcaaa-150">Dans l'runtimeconfig.template.jsde l’application *sur* le fichier :</span><span class="sxs-lookup"><span data-stu-id="fcaaa-150">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="fcaaa-151">Si vous réactivez la prise en charge d’UTF-7, vous devez effectuer une révision de sécurité du code qui appelle <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fcaaa-151">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="fcaaa-152">Category</span><span class="sxs-lookup"><span data-stu-id="fcaaa-152">Category</span></span>

- <span data-ttu-id="fcaaa-153">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="fcaaa-153">Core .NET libraries</span></span>
- <span data-ttu-id="fcaaa-154">Sécurité</span><span class="sxs-lookup"><span data-stu-id="fcaaa-154">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fcaaa-155">API affectées</span><span class="sxs-lookup"><span data-stu-id="fcaaa-155">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
