---
title: Nouveautés du .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: f56ba7d68be107e697d3f732767f0a5f11c1a622
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644228"
---
# <a name="whats-new-in-net-framework"></a>Quoi de neuf dans le cadre .NET

Cet article résume les principales nouvelles fonctionnalités et améliorations des versions suivantes du .NET Framework :

- [.NET Framework 4.8](#v48)
- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 et .NET Framework 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Cet article ne fournit pas d'informations complètes sur chacune des nouvelles fonctionnalités et peut faire l'objet de modifications. Pour obtenir des informations générales sur le .NET Framework, consultez [Prise en main](../get-started/index.md). Pour connaître les plateformes prises en charge, consultez [Configuration requise](../get-started/system-requirements.md). Pour obtenir des liens de téléchargement et des instructions d’installation, consultez [Guide d’installation](../install/guide-for-developers.md).

> [!NOTE]
> L’équipe .NET Framework publie aussi des fonctionnalités hors bande avec NuGet pour étendre la prise en charge des plateformes et introduire des nouveautés, telles que les collections immuables et les types de vecteurs compatibles SIMD. Pour plus d’informations, consultez [Autres bibliothèques de classes et API](../additional-apis/index.md) et [Versions finales hors plage de .NET Framework](../get-started/the-net-framework-and-out-of-band-releases.md).
> Consultez la [liste complète des packages NuGet](https://www.nuget.org/profiles/dotnetframework) pour .NET Framework.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>Présentation de .NET Framework 4.8

.NET Framework 4.8 repose sur les versions précédentes de .NET Framework 4.x, auxquelles il ajoute un grand nombre de nouveaux correctifs et plusieurs nouvelles fonctionnalités, tout en restant un produit très stable.

### <a name="downloading-and-installing-net-framework-48"></a>Téléchargement et installation de .NET Framework 4.8

Vous pouvez télécharger .NET Framework 4.8 aux emplacements suivants :

- [Programme d’installation web de .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [Programme d’installation hors connexion de .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

.NET Framework 4.8 peut être installé sur Windows 10, Windows 8.1, Windows 7 SP1 et les plateformes de serveur correspondantes à partir de Windows Server 2008 R2 SP1. Vous pouvez installer .NET Framework 4.8 à l’aide du programme d’installation web ou du programme d’installation hors connexion. Le programme d’installation web constitue la méthode recommandée pour la plupart des utilisateurs.

Vous pouvez cibler .NET Framework 4.8 dans Visual Studio 2012 ou ultérieur en installant [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>Nouveautés de .NET Framework 4.8

.NET Framework 4.8 introduit de nouvelles fonctionnalités dans les domaines suivants :

- [Classes de base](#core48)
- [Fondation De communication Windows (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Temps courant de la langue](#clr48)

L’amélioration de l’accessibilité, pour qu’une application puisse fournir une expérience appropriée aux utilisateurs de technologies d’assistance, reste un objectif majeur de .NET Framework 4.8. Pour plus d’informations sur les améliorations apportées à .NET Framework 4.8 dans le domaine de l’accessibilité, consultez [Nouveautés du .NET Framework dans le domaine de l’accessibilité](whats-new-in-accessibility.md).

<a name="core48" />

#### <a name="base-classes"></a>Classes de base

**Impact FIPS réduit sur le chiffrement**. Dans les versions précédentes du .NET Framework, des classes de fournisseur de services de chiffrement managées telles que <xref:System.Security.Cryptography.SHA256Managed> levaient une exception <xref:System.Security.Cryptography.CryptographicException> lorsque les bibliothèques de chiffrement du système étaient configurées en « mode FIPS ». Ces exceptions étaient levées car les versions managées des classes de fournisseur de services de chiffrement, contrairement aux bibliothèques de chiffrement du système, ne disposaient pas de la certification de normes FIPS (Federal Information Processing Standard) 140-2. Peu de développeurs disposant de machines de développement en mode FIPS, les exceptions étaient généralement levées dans des systèmes de production.

Par défaut, dans les applications ciblant .NET Framework 4.8, les classes de chiffrement managées suivantes ne lèvent plus une exception <xref:System.Security.Cryptography.CryptographicException> dans ce cas :

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Ces classes redirigent plutôt les opérations de chiffrement vers une bibliothèque de chiffrement du système. Cette modification supprime efficacement une différence pouvant potentiellement prêter à confusion entre les environnements de développement et les environnements de production, et permet d’exécuter les composants natifs et les composants managés sous la même stratégie de chiffrement. Les applications qui dépendent de ces exceptions peuvent restaurer le comportement précédent en définissant le commutateur AppContext `Switch.System.Security.Cryptography.UseLegacyFipsThrow` sur `true`. Pour plus d’informations, consultez [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode) (Les classes de chiffrement managées ne lèvent pas d’exception de chiffrement en mode FIPS).

**Utilisation d’une version mise à jour de ZLib**

À compter de .NET Framework 4.5, l’assembly clrcompression.dll utilise [ZLib](https://www.zlib.net), une bibliothèque externe native de compression de données, afin de fournir une implémentation de l’algorithme deflate. Dans .NET Framework 4.8, clrcompression.dll est mis à jour pour utiliser ZLib version 1.2.11, qui inclut plusieurs améliorations et correctifs clés.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Présentation de ServiceHealthBehavior**

Les points de terminaison d’intégrité sont couramment utilisés par les outils d’orchestration pour gérer les services en fonction de leur état d’intégrité. Des vérifications de l’intégrité peuvent également être utilisées par les outils d’analyse pour suivre et fournir des notifications sur la disponibilité et les performances d’un service.

**ServiceHealthBehavior** est un comportement de service WCF qui étend <xref:System.ServiceModel.Description.IServiceBehavior>.  Lorsqu’il est ajouté à la collection <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType>, un comportement de service effectue les opérations suivantes :

- Retourne l’état d’intégrité du service avec des codes de réponse HTTP. Vous pouvez spécifier dans une chaîne de requête le code d’état HTTP d’une requête de sonde d’intégrité HTTP/GET.

- Publie des informations sur l’intégrité du service. Des informations spécifiques du service, y compris l’état du service, le nombre de limitations et la capacité, peuvent être affichées à l’aide d’une requête HTTP/GET avec la chaîne de requête `?health`. Il est important de pouvoir accéder facilement à ces informations lors de la résolution des problèmes liés à un service WCF se comportant anormalement.

Deux méthodes permettent d’exposer le point de terminaison d’intégrité et de publier les informations d’intégrité du service WCF :

- Par le biais du code. Par exemple :

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- À l’aide d’un fichier de configuration. Par exemple :

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

L’état d’intégrité d’un service peut être interrogé à l’aide de paramètres de requête tels que `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`, et un code de réponse HTTP peut être spécifié pour chaque paramètre de requête. Si le code de réponse HTTP est omis pour un paramètre de requête, un code de réponse HTTP 503 est utilisé par défaut. Par exemple :

- OnServiceFailure : `https://contoso:81/Service1?health&OnServiceFailure=450`

  Un code d’état de réponse HTTP 450 est retourné lorsque [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) est supérieur à <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.
Paramètres de requête et exemples :

- OnDispatcherFailure : `https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Un code d’état de réponse HTTP 455 est retourné lorsque l’état de l’un des répartiteurs de canal est supérieur à <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnListenerFailure : `https://contoso:81/Service1?health&OnListenerFailure=465`

  Un code d’état de réponse HTTP 465 est retourné lorsque l’état de l’un des écouteurs de canal est supérieur à <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnThrottlePercentExceeded : `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Spécifie le pourcentage {1 – 100} qui déclenche la réponse et son code de réponse HTTP {200 – 599}. Dans cet exemple :

  - Si le pourcentage est supérieur à 95, un code de réponse HTTP 500 est retourné.

  - Si le pourcentage est compris entre 70 et 95, un code de réponse 350 est retourné.

  - Sinon, un code de réponse 200 est retourné.

L’état d’intégrité du service peut être affiché au format HTML en spécifiant une chaîne de requête telle que `https://contoso:81/Service1?health` ou au format XML en spécifiant une chaîne de requête telle que `https://contoso:81/Service1?health&Xml`. Une chaîne de requête telle que `https://contoso:81/Service1?health&NoContent` retourne une page HTML vide.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Améliorations de la haute résolution**

Dans .NET Framework 4.8, WPF ajoute la prise en charge DPI V2 par moniteur et la mise à l’échelle PPP en mode mixte. Consultez [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) (Développement d’applications de bureau haute résolution sur Windows) pour plus d’informations sur le développement de la haute résolution.

.NET framework 4.8 améliore la prise en charge pour l’interopérabilité de HWND et de Windows Forms hébergés dans des applications WPF haute résolution sur les plateformes qui prennent en charge la mise à l’échelle PPP en mode mixte (depuis la Mise à jour d’avril 2018 de Windows 10). Lorsque des contrôles HWND ou Windows Forms hébergés sont créés en tant que fenêtres mises à l’échelle PPP en mode en appelant [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) et [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), ils peuvent être hébergés dans une application WPF V2 par moniteur, et sont dimensionnés et mis à l’échelle de manière appropriée. Ce type de contenu hébergé n’est pas restitué à la résolution native ; le système d’exploitation met à l’échelle le contenu hébergé à la taille appropriée. La prise en charge du mode de prise en charge DPI V2 par moniteur permet également d’héberger des contrôles WPF (par exemple, apparentés) dans une fenêtre d’une application haute résolution.

Pour activer la prise en charge de la mise à l’échelle de la haute résolution en mode mixte, vous pouvez définir les commutateurs [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier de configuration de l’application :

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Common Language Runtime

Le runtime de .NET Framework 4.8 comprend les nouvelles modifications et améliorations suivantes :

**Améliorations apportées au compilateur JIT**. Le compilateur juste-à-temps (JIT) de .NET Framework 4.8 est basé sur le compilateur JIT de .NET Core 2.1. La plupart des optimisations et tous les correctifs de bogues apportés au compilateur JIT de .NET Core 2.1 sont inclus dans le compilateur JIT de .NET Framework 4.8.

**Améliorations apportées à NGEN**. La gestion de la mémoire du runtime a été améliorée pour les images [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) afin que les données mappées à partir d’images NGEN ne résident pas en mémoire. Cela réduit la surface d’exposition aux attaques qui tentent d’exécuter du code arbitraire en modifiant la mémoire qui sera exécutée.

**Analyse de logiciel anti-programme malveillant pour tous les assemblys**. Dans les versions précédentes du .NET Framework, le runtime analyse tous les assemblys chargés à partir du disque à l’aide de Windows Defender ou d’un logiciel anti-programme malveillant tiers. Les assemblys chargés à partir d’autres sources, via la méthode <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> par exemple, ne sont toutefois pas analysés et sont susceptibles de contenir des programmes malveillants non détectés. À compter de .NET Framework 4.8 exécuté sur Windows 10, le runtime déclenche une analyse via des solutions anti-programme malveillant qui implémentent l’[interface d’analyse anti-programme malveillant (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>Nouveautés de .NET Framework 4.7.2

.NET Framework 4.7.2 apporte de nouvelles fonctionnalités dans les domaines suivants :

- [Classes de base](#core-472)
- [ASP.NET](#asp-net472)
- [Mise en réseau](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

.NET Framework 4.7.2 met l’accent sur l’amélioration de l’accessibilité pour qu’une application puisse fournir une expérience appropriée aux utilisateurs de technologies d’assistance. Pour plus d’informations sur les améliorations apportées à .NET Framework 4.7.2 dans le domaine de l’accessibilité, consultez [Nouveautés du .NET Framework dans le domaine de l’accessibilité](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="base-classes"></a>Classes de base

.NET Framework 4.7.2 propose un grand nombre d’améliorations de chiffrement, une meilleure prise en charge de la décompression des archives ZIP et de nouvelles API de collection.

**Nouvelles surcharges de RSA.Create et DSA.Create**

Les méthodes <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> et <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> permettent d’indiquer des paramètres de clés en cas d’instanciation d’une nouvelle clé <xref:System.Security.Cryptography.DSA> ou <xref:System.Security.Cryptography.RSA>. Elles vous permettent de remplacer du code tel que le suivant :

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

par du code comme celui-ci :

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

Les méthodes <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> et <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> vous permettent de générer de nouvelles clés <xref:System.Security.Cryptography.DSA> ou <xref:System.Security.Cryptography.RSA> avec une taille de clé spécifique. Par exemple :

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

**Les constructeurs Rfc2898DeriveBytes acceptent un nom d’algorithme de hachage**

La classe <xref:System.Security.Cryptography.Rfc2898DeriveBytes> a trois nouveaux constructeurs avec un paramètre <xref:System.Security.Cryptography.HashAlgorithmName> qui identifie l’algorithme HMAC à utiliser lors de la dérivation de clés. Au lieu d’utiliser SHA-1, les développeurs doivent utiliser un algorithme HMAC basé sur SHA-2, tel que SHA-256, comme indiqué dans l’exemple suivant :

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

**Prise en charge des clés éphémères**

L’importation PFX peut éventuellement charger des clés privées directement à partir de la mémoire, en ignorant le disque dur.Quand le nouvel indicateur <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> est spécifié dans un constructeur <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> ou l’une des surcharges de la méthode <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType>, les clés privées sont chargées en tant que clés éphémères. Cela empêche que les clés soient visibles sur le disque. Toutefois :

- Étant donné que les clés ne sont pas conservées sur le disque, les certificats chargés avec cet indicateur ne sont pas de bons candidats pour être ajoutés à un X509Store.

- Les clés chargées de cette manière le sont presque toujours par Windows CNG. Ainsi, les appelants doivent accéder à la clé privée en appelant des méthodes d’extension, telles que [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). La propriété <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> ne fonctionne pas.

- Puisque la propriété <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> héritée ne fonctionne pas avec les certificats, les développeurs doivent effectuer des tests rigoureux avant de passer aux clés éphémères.

**Création par programmation de demandes de signature de certification PKCS#10 et de certificats de clé publique X.509**

À compter de .NET Framework 4.7.2, les charges de travail peuvent générer des demandes de signature de certificat, ce qui permet de générer une demande de certificat dans des outils existants. C’est souvent utile dans les scénarios de test.

Pour plus d’informations et des exemples de code, consultez « Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates » sur le [Blog .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Nouveaux membres SignerInfo**

À compter de .NET Framework 4.7.2, la classe <xref:System.Security.Cryptography.Pkcs.SignerInfo> expose davantage d’informations sur la signature. Vous pouvez récupérer la valeur de la propriété <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> pour déterminer l’algorithme de signature utilisé par le signataire. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> peut être appelée afin d’obtenir une copie de la signature de chiffrement pour ce signataire.

**Laisser un flux encapsulé ouvert après la suppression de CryptoStream**

À compter de .NET Framework 4.7.2, la classe <xref:System.Security.Cryptography.CryptoStream> a un constructeur supplémentaire qui permet à <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> de ne pas fermer le flux wrappé.Pour laisser le flux wrappé ouvert après la suppression de l’instance <xref:System.Security.Cryptography.CryptoStream>, appelez le nouveau constructeur <xref:System.Security.Cryptography.CryptoStream> comme suit :

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**Changements de décompression dans DeflateStream**

À compter de .NET Framework 4.7.2, l’implémentation des opérations de décompression de la classe <xref:System.IO.Compression.DeflateStream> a été changée de façon à utiliser des API Windows natives par défaut. En règle générale, s’ensuit une amélioration sensible des performances.

La prise en charge de la décompression à l’aide des API Windows est activée par défaut pour les applications qui ciblent .NET Framework 4.7.2. Les applications qui ciblent les versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.7.2 peuvent adopter ce comportement en ajoutant le [commutateur AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant au fichier de configuration d’application :

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**API de collection supplémentaires**

.NET Framework 4.7.2 ajoute de nouvelles API aux types <xref:System.Collections.Generic.SortedSet%601> et <xref:System.Collections.Generic.HashSet%601>. notamment :

- Des méthodes `TryGetValue` qui étendent le modèle try utilisé dans d’autres types de collection à ces deux types. Ces méthodes sont les suivantes :

  - [bool public HashSet\<T>. TryGetValue (T equalValue, T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [bool public SortedSet\<T>. TryGetValue (T equalValue, T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- Des méthodes d’extension `Enumerable.To*` qui convertissent une collection en <xref:System.Collections.Generic.HashSet%601> :

  - [public statique HashSet\<TSource> ToHashSet\<TSource> (cette source\<IEnumerable TSource>)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [public\<statique HashSet TSource> ToHashSet\<TSource> (cette source\<IEnumerable TSource>, IEqualityComparer\<TSource> comparer)](xref:System.Linq.Enumerable.ToHashSet%2A)

- De nouveaux constructeurs <xref:System.Collections.Generic.HashSet%601> qui vous permettent de définir la capacité de la collection, ce qui génère un gain de performances quand vous connaissez à l’avance la taille de <xref:System.Collections.Generic.HashSet%601> :

  - [public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [public HashSet (capacité int, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

La classe <xref:System.Collections.Concurrent.ConcurrentDictionary%602> comprend de nouvelles surcharges des méthodes <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> et <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> pour récupérer une valeur à partir du dictionnaire ou l’ajouter si elle est introuvable, et pour ajouter une valeur au dictionnaire ou la mettre à jour si elle existe déjà.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a>ASP.NET

**Prise en charge de l’injection de dépendances dans Web Forms**

L’[injection de dépendances](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) dissocie les objets et leurs dépendances afin qu’il ne soit plus obligatoire de modifier le code d’un objet simplement parce qu’une dépendance a changé. Lors du développement d’applications ASP.NET qui ciblent .NET Framework 4.7.2, vous pouvez :

- Utiliser l’injection basée sur méthode setter, sur interface et sur constructeur dans des [gestionnaires et des modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), des [instances de pages](xref:System.Web.UI.Page) et des [contrôles utilisateur](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) de projets d’applications web ASP.NET.

- Utiliser l’injection basée sur méthode setter et sur interface dans des [gestionnaires et des modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), des [instances de pages](xref:System.Web.UI.Page) et des [contrôles utilisateur](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) de projets de sites web ASP.NET.

- Raccorder différents frameworks d’injection de dépendances.

**Prise en charge des cookies du même site**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) empêche un navigateur d’envoyer un cookie avec une requête intersite. .NET Framework 4.7.2 ajoute une propriété <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> dont la valeur est un membre d’énumération <xref:System.Web.SameSiteMode?displayProperty=nameWithType>. Si sa valeur est <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> ou <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET ajoute l’attribut `SameSite` à l’en-tête set-cookie. La prise en charge de SameSite s’applique aux objets <xref:System.Web.HttpCookie>, ainsi qu’aux cookies <xref:System.Web.Security.FormsAuthentication> et <xref:System.Web.SessionState>.

Vous pouvez définir SameSite pour un objet <xref:System.Web.HttpCookie> comme suit :

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Vous pouvez également configurer des cookies SameSite au niveau de l’application en modifiant le fichier web.config :

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Vous pouvez ajouter SameSite pour des cookies <xref:System.Web.Security.FormsAuthentication> et <xref:System.Web.SessionState> en modifiant le fichier de configuration web :

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Mise en réseau

**Implémentation des propriétés HttpClientHandler**

.NET Framework 4.7.1 a ajouté huit propriétés à la classe <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>. Toutefois, deux d’entre elles levaient une <xref:System.PlatformNotSupportedException>. .NET Framework 4.7.2 fournit désormais une implémentation pour ces propriétés. Les propriétés sont les suivantes :

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Prise en charge de l’authentification universelle Azure Active Directory et de l’authentification multifacteur**

Face aux exigences croissantes de conformité et de sécurité, de nombreux clients se voient obligés d’utiliser l’authentification multifacteur (MFA). De plus, les bonnes pratiques en vigueur n’encouragent pas la saisie des mots de passe utilisateur directement dans les chaînes de connexion. Pour gérer ces changements, .NET Framework 4.7.2 étend les [chaînes de connexion SQLClient](xref:System.Data.SqlClient.SqlConnection.ConnectionString) en ajoutant une nouvelle valeur, « Active Directory Interactive », pour le mot clé « Authentification » existant afin de prendre en charge MFA et [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure). La nouvelle méthode interactive prend en charge les utilisateurs Azure AD natifs et fédérés, ainsi que les utilisateurs invités Azure AD. Quand cette méthode est utilisée, l’authentification MFA imposée par Azure AD est prise en charge pour les bases de données SQL. De plus, le processus d’authentification demande un mot de passe utilisateur afin de respecter les bonnes pratiques de sécurité.

Dans les versions précédentes du .NET Framework, la connectivité SQL prenait uniquement en charge les options <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> et <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType>. Toutes deux font partie du [protocole ADAL](/azure/active-directory/develop/active-directory-authentication-libraries) non interactif, qui ne prend pas en charge MFA. Avec la nouvelle option <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType>, la connectivité SQL prend en charge MFA ainsi que les méthodes d’authentification existantes (authentification intégrée et par mot de passe), ce qui permet aux utilisateurs d’entrer les mots de passe utilisateur de manière interactive sans les conserver dans la chaîne de connexion.

Pour plus d’informations et pour obtenir un exemple, consultez « SQL -- Azure AD Universal and Multi-factor Authentication Support » sur le [Blog .NET](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Prise en charge d’Always Encrypted version 2**

.NET Framework 4.7.2 ajoute la prise en charge d’Always Encrypted basé sur enclave. La version d’origine d’Always Encrypted est une technologie de chiffrement côté client dans laquelle les clés de chiffrement ne quittent jamais le client. Avec Always Encrypted basé sur enclave, le client peut s’il le souhaite envoyer les clés de chiffrement à une enclave sécurisée, qui est une entité de calcul sécurisée pouvant être considérée comme faisant partie de SQL Server, mais que le code SQL Server ne peut pas falsifier. Pour prendre en charge Always Encrypted basé sur enclave, .NET Framework 4.7.2 ajoute les types et membres suivants à l’espace de noms <xref:System.Data.SqlClient> :

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, qui spécifie l’URI pour Always Encrypted basé sur enclave.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, qui est une classe abstraite à partir de laquelle tous les fournisseurs d’enclave sont dérivés.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, qui encapsule l’état d’une session d’enclave donnée.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, qui fournit les paramètres d’attestation utilisés par SQL Server afin d’obtenir les informations requises pour exécuter un protocole d’attestation spécifique.

Le fichier de configuration d’application spécifie ensuite une implémentation concrète de la classe <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> abstraite qui fournit la fonctionnalité pour le fournisseur d’enclave. Par exemple :

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

Le flux de base d’Always Encrypted basé sur enclave est le suivant :

1. L’utilisateur crée une connexion AlwaysEncrypted à SQL Server qui prend en charge Always Encrypted basé sur enclave. Le pilote contacte le service d’attestation pour s’assurer qu’il se connecte à la bonne enclave.

1. Une fois l’enclave attestée, le pilote établit un canal sécurisé avec l’enclave sécurisée hébergée sur SQL Server.

1. Le pilote partage les clés de chiffrement autorisées par le client avec l’enclave sécurisée pendant la durée de la connexion SQL.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Recherche de ResourceDictionaries par source**

À compter de .NET Framework 4.7.2, un Assistant de diagnostic peut localiser les  <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> qui ont été créés à partir d’un URI source donné.(Cette fonctionnalité est destinée aux assistants diagnostiques, et non aux applications de production.) Un assistant diagnostique tel que l’installation « Edit-and-Continue » de Visual Studio permet à son utilisateur de modifier un ResourceDictionary dans l’intention d’appliquer les modifications à l’application en cours d’exécution. Dans ce but, l’une des étapes consiste à trouver tous les ResourceDictionaries créés par l’application en cours d’exécution à partir du dictionnaire en cours de modification. Par exemple, une application peut déclarer un ResourceDictionary dont le contenu est copié à partir d’un URI source donné :

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

Un assistant diagnostique qui modifie la majoration originale dans *MyRD.xaml* peut utiliser la nouvelle fonctionnalité pour localiser le dictionnaire.La fonctionnalité est implémentée par une nouvelle méthode statique, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>. L’Assistant de diagnostic appelle la nouvelle méthode à l’aide d’un URI absolu qui identifie le balisage d’origine, comme illustré par le code suivant :

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

La méthode renvoie un vide <xref:System.Windows.Diagnostics.VisualDiagnostics> enumerable à moins d’être activé et la variable de l’environnement [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  est définie.

**Recherche de propriétaires de ResourceDictionary**

À compter de .NET Framework 4.7.2, un Assistant de diagnostic peut localiser les propriétaires d’un <xref:Windows.UI.Xaml.ResourceDictionary> donné.(La fonction est utilisée par les assistants diagnostiques et non par les applications de production.) Chaque fois qu’un <xref:Windows.UI.Xaml.ResourceDictionary>changement est apporté à un , WPF trouve automatiquement toutes les références [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) qui pourraient être affectées par le changement.

Un assistant diagnostique tel que l’installation « Edit-and-Continue » de Visual Studio peut vouloir étendre cette extension pour traiter les références [StaticResource.](../wpf/advanced/staticresource-markup-extension.md) La première étape de ce processus consiste à rechercher les propriétaires du dictionnaire, autrement dit à rechercher tous les objets dont la propriété `Resources` fait référence au dictionnaire (directement ou indirectement par le biais de la propriété <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType>). Trois nouvelles méthodes statiques implémentées sur la classe <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType>, une pour chacun des types de base ayant une propriété `Resources`, prennent en charge cette étape :

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Ces méthodes renvoient un vide <xref:System.Windows.Diagnostics.VisualDiagnostics> enumerable à moins d’être activé et la variable de l’environnement [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  est définie.

**Recherche de références StaticResource**

Un Assistant de diagnostic peut maintenant recevoir une notification chaque fois qu’une référence [StaticResource](../wpf/advanced/staticresource-markup-extension.md) est résolue.(La fonction est utilisée par les assistants diagnostiques, et non par des applications de production.) Un assistant diagnostique tel que l’installation « Edit-and-Continue » de Visual Studio peut <xref:Windows.UI.Xaml.ResourceDictionary> vouloir mettre à jour toutes les utilisations d’une ressource lorsque sa valeur dans un changement. WPF le fait automatiquement pour les références [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md), mais il ne le fait pas (intentionnellement) pour les références [StaticResource](../wpf/advanced/staticresource-markup-extension.md). À compter de .NET Framework 4.7.2, l’Assistant de diagnostic peut utiliser ces notifications pour localiser ces utilisations de la ressource statique.

La notification est implémentée par le nouvel événement <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> :

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Cet événement est déclenché chaque fois que le runtime résout une référence [StaticResource](../wpf/advanced/staticresource-markup-extension.md).Les arguments <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> décrivent la résolution et indiquent l’objet et la propriété qui hébergent la référence [StaticResource](../wpf/advanced/staticresource-markup-extension.md) ainsi que la clé  <xref:Windows.UI.Xaml.ResourceDictionary> utilisée pour la résolution :

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

L’événement n’est `add` pas soulevé (et <xref:System.Windows.Diagnostics.VisualDiagnostics> son accesseur est ignoré) à moins d’être activé et la variable de l’environnement [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  est définie.

#### <a name="clickonce"></a>ClickOnce

Les applications avec prise en charge HDPI pour Windows Forms, WPF (Windows Presentation Foundation) et VSTO (Visual Studio Tools pour Office) peuvent toutes être déployées à l’aide de ClickOnce. Si l’entrée suivante est détectée dans le manifeste d’application, le déploiement réussit dans .NET Framework 4.7.2 :

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Pour une application Windows Forms, la solution de contournement précédente consistant à définir la prise en charge DPI dans le fichier de configuration d’application plutôt que dans le manifeste d’application n’est plus nécessaire à la réussite du déploiement ClickOnce.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>Nouveautés du .NET Framework 4.7.1

.NET Framework 4.7.1 apporte de nouvelles fonctionnalités dans les domaines suivants :

- [Classes de base](#core471)
- [Temps courant (CLR)](#clr)
- [Mise en réseau](#net471)
- [ASP.NET](#asp-net471)

.NET Framework 4.7.1 met également l’accent sur l’amélioration de l’accessibilité pour qu’une application puisse fournir une expérience appropriée aux utilisateurs de technologies d’assistance. Pour plus d’informations sur les améliorations apportées à .NET Framework 4.7.1 dans le domaine de l’accessibilité, consultez [Nouveautés du .NET Framework dans le domaine de l’accessibilité](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="base-classes"></a>Classes de base

**Prise en charge de .NET 2.0 Standard**

[.NET Standard](../../standard/net-standard.md) définit un ensemble d’API qui doivent être disponibles sur chaque implémentation .NET prenant en charge cette version de la norme. .NET Framework 4.7.1 prend entièrement en charge .NET Standard 2.0 et ajoute [200 API environ](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) qui sont définies dans .NET Standard 2.0 et qui ne figurent pas dans .NET Framework 4.6.1, 4.6.2 et 4.7. (Notez que ces versions du support .NET Framework .NET Standard 2.0 seulement si des fichiers de support .NET Standard supplémentaires sont également déployés sur le système cible.) Pour plus d’informations, voir "BCL - .NET Standard 2.0 Support" dans le [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.

**Prise en charge des générateurs de configuration**

Les générateurs de configuration permettent aux développeurs d’injecter et de générer dynamiquement des paramètres de configuration pour les applications au moment de l’exécution. Des générateurs de configuration personnalisés peuvent être utilisés pour modifier des données existantes dans une section de configuration ou générer une section de configuration entièrement nouvelle. Sans les générateurs de configuration, les fichiers .config sont statiques, et leurs paramètres sont définis avant le lancement d’une application.

Pour créer un générateur de configuration personnalisé, dérivez votre générateur de la classe abstraite <xref:System.Configuration.ConfigurationBuilder> et substituez <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> et <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Vous pouvez également définir vos générateurs dans votre fichier .config. Pour plus d’informations, consultez la section « Configuration Builders » dans le billet de blog [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/).

**Détection des fonctionnalités au moment de l’exécution**

La classe <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> fournit un mécanisme pour déterminer si une fonctionnalité prédéfinie est prise en charge sur une implémentation .NET donnée au moment de la compilation ou de l’exécution. Au moment de la compilation, un compilateur peut vérifier l’existence d’un champ spécifié pour déterminer si la fonctionnalité est prise en charge. Dans l’affirmative, il peut émettre du code qui exploite cette fonctionnalité. Au moment de l’exécution, une application peut appeler la méthode <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> avant d’émettre du code. Pour plus d’informations, consultez [Ajouter une méthode d’assistance pour décrire les fonctionnalités prises en charge par le runtime](https://github.com/dotnet/corefx/issues/17116).

**Les types tuple de valeur sont sérialisables**

À compter de .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> et ses types génériques associés sont marqués comme [sérialisables](xref:System.SerializableAttribute), ce qui permet une sérialisation binaire. Cela doit faciliter la migration des types Tuple, comme <xref:System.Tuple%603> et <xref:System.Tuple%604>, vers des types tuple de valeur. Pour plus d’informations, consultez « Compiler -- ValueTuple is Serializable » dans le billet de blog [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/).

**Prise en charge des références en lecture seule**

.NET framework 4.7.1 ajoute le <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Cet attribut est utilisé par les compilateurs de langage pour marquer les membres qui ont des paramètres ou des types de retour de référence en lecture seule. Pour plus d’informations, consultez « Compiler -- Support for ReadOnlyReferences » dans le billet de blog [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/). Pour plus d’informations sur les valeurs de retour de référence, consultez [Valeurs de retour de référence et variables locales ref (Guide C#)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) et [Valeurs de retour de référence (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Common Language Runtime (CLR)

**Amélioration des performances du garbage collection**

Les modifications apportées à la collecte des ordures (GC) dans le cadre .NET 4.7.1 améliorent les performances globales, en particulier pour les allocations de tas d’objets volumines (LOH). Dans .NET Framework 4.7.1, des serrures séparées sont utilisées pour les allocations de tas de petits objets (SOH) et LOH, ce qui permet aux allocations LOH de se produire lorsque le GC de fond balaie le SOH. Les applications qui créent un grand nombre d’allocations LOH bénéficient donc d’une réduction de la contention de verrouillage des allocations et de meilleures performances. Pour plus d’informations, consultez la section « Runtime -- GC Performance Improvements » dans le billet de blog [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/).

<a name="net471"/>

#### <a name="networking"></a>Mise en réseau

**Prise en charge de SHA-2 pour Message.HashAlgorithm**

Dans .NET Framework 4.7 et versions antérieures, la propriété <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> prenait uniquement en charge les valeurs <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> et <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType>. À compter de .NET Framework 4.7.1, les valeurs <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType> et <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> sont également prises en charge. MSMQ détermine si cette valeur est utilisée ou non, puisque l’instance de <xref:System.Messaging.Message> n’effectue elle-même aucun hachage et passe simplement les valeurs à MSMQ. Pour plus d’informations, consultez la section « SHA-2 support for Message.HashAlgorithm » dans le billet de blog [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/).

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**Étapes d’exécution dans les applications ASP.NET**

ASP.NET traite les demandes dans un pipeline prédéfini comprenant 23 événements. ASP.NET exécute chaque gestionnaire d’événements sous forme d’étape d’exécution. Dans les versions d’ASP.NET jusqu’à .NET Framework 4.7, ASP.NET ne peut pas passer le contexte d’exécution en raison de la commutation entre threads natifs et threads managés. Au lieu de cela, ASP.NET passe uniquement <xref:System.Web.HttpContext> de manière sélective. À compter de .NET Framework 4.7.1, la méthode <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> permet également aux modules de restaurer les données ambiantes. Cette fonctionnalité est destinée aux bibliothèques préoccupées par le traçage, le profilage, les diagnostics ou les transactions qui, par exemple, tiennent compte du flux d’exécution de l’application. Pour plus d’informations, consultez « ASP.NET Execution Step Feature » dans le billet de blog [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/).

**Analyse HttpCookie ASP.NET**

.NET Framework 4.7.1 comprend une nouvelle méthode, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, qui offre un moyen normalisé de créer un objet <xref:System.Web.HttpCookie> à partir d’une chaîne et d’affecter avec précision des valeurs de cookie telles que la date d’expiration et le chemin. Pour plus d’informations, consultez « ASP.NET HttpCookie parsing » dans le billet de blog [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/).

**Options de hachage SHA-2 pour les informations d’identification de l’authentification par formulaires ASP.NET**

Dans .NET Framework 4.7 et versions antérieures, ASP.NET permettait aux développeurs de stocker les informations d’identification des utilisateurs avec des mots de passe hachés dans des fichiers de configuration en utilisant MD5 ou SHA-1. À compter de .NET Framework 4.7.1, ASP.NET prend en charge de nouvelles options de hachage SHA-2 sécurisées, notamment SHA256, SHA384 et SHA512. SHA1 reste la valeur par défaut, et un algorithme de hachage autre que celui par défaut peut être défini dans le fichier de configuration web. Par exemple :

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47" />

## <a name="whats-new-in-net-framework-47"></a>Nouveautés de .NET Framework 4.7

.NET Framework 4.7 apporte de nouvelles fonctionnalités dans les domaines suivants :

- [Classes de base](#Core47)
- [Mise en réseau](#net47)
- [ASP.NET](#ASP-NET47)
- [Fondation De communication Windows (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Pour obtenir la liste des nouvelles API ajoutées à .NET Framework 4.7, consultez la page [Changements au niveau des API de .NET Framework 4.7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) sur GitHub. Pour obtenir la liste des fonctionnalités améliorées et des correctifs de bogues apportés à .NET Framework 4.7, consultez la page [Liste des changements de .NET Framework 4.7](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) sur GitHub. Pour plus d’informations, voir [Annoncez le .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) dans le blog .NET.

<a name="Core47" />

#### <a name="base-classes"></a>Classes de base

.NET Framework 4.7 améliore la sérialisation par le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> :

**Fonctionnalité améliorée avec Cryptographie de courbe elliptique (ECC)***

Dans .NET Framework 4.7, des méthodes `ImportParameters(ECParameters)` ont été ajoutées aux classes <xref:System.Security.Cryptography.ECDsa> et <xref:System.Security.Cryptography.ECDiffieHellman> pour permettre à un objet de représenter une clé déjà établie. En outre, une méthode `ExportParameters(Boolean)` a été ajoutée pour exporter la clé à l’aide de paramètres de courbes explicites.

.NET Framework 4.7 ajoute également la prise en charge de courbes supplémentaires (notamment la série de courbes Brainpool) et intègre des définitions prédéfinies pour faciliter la création via les nouvelles méthodes de fabrique <xref:System.Security.Cryptography.ECDsa.Create%2A> et <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A>.

Vous pouvez voir un [exemple des améliorations apportées au chiffrement de .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) sur GitHub.

**Meilleure prise en charge des caractères de contrôle par le DataContractJsonSerializer**

Dans .NET Framework 4.7, la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> classe sérialis les personnages de contrôle conformément à la norme ECMAScript 6. Ce comportement est activé par défaut pour les applications qui ciblent .NET Framework 4.7, et est une fonctionnalité d’opt-in pour les applications qui sont en cours d’exécution sous .NET Framework 4.7 mais ciblent une version précédente de .NET Framework. Pour plus d’informations, consultez la section [compatibilité de l’application.](../migration-guide/application-compatibility.md)

<a name="net47" />

#### <a name="networking"></a>Mise en réseau

.NET Framework 4.7 ajoute les fonctionnalités liées au réseau suivantes :

**Support système d’exploitation par défaut pour les protocoles TLS***

La pile TLS, qui est utilisée par <xref:System.Net.Security.SslStream?displayProperty=nameWithType> et les composants au-dessus de la pile, comme HTTP, FTP et SMTP, permet aux développeurs d’utiliser les protocoles TLS par défaut pris en charge par le système d’exploitation. Les développeurs n’ont plus besoin de coder en dur une version TLS.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

Dans .NET Framework 4.7, ASP.NET propose les nouvelles fonctionnalités suivantes :

**Extensibilité du cache d’objets**

À compter de .NET Framework 4.7, ASP.NET ajoute un nouvel ensemble d’API permettant aux développeurs de remplacer les implémentations ASP.NET par défaut pour la mise en cache d’objets en mémoire et la surveillance de la mémoire. Les développeurs peuvent maintenant remplacer un des trois composants suivants si l’implémentation ASP.NET n’est pas appropriée :

- **Object Cache Store**. À l’aide de la nouvelle section de configuration des fournisseurs de cache, les développeurs peuvent incorporer de nouvelles implémentations d’un cache d’objets pour une application ASP.NET en utilisant la nouvelle interface **ICacheStoreProvider**.

- **Surveillance de la mémoire**. Le moniteur de mémoire par défaut dans ASP.NET avertit les applications lorsqu’elles approchent la limite en octets privés définie pour le processus, ou lorsque la machine manque de mémoire RAM physique disponible. Lorsque ces limites sont proches, des notifications sont déclenchées. Pour certaines applications, les notifications sont déclenchées trop près des limites configurées pour permettre des réactions opportunes. Les développeurs peuvent désormais écrire leurs propres moniteurs de mémoire pour remplacer le moniteur par défaut en utilisant la propriété <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType>.

- **Memory Limit Reactions**. Par défaut, ASP.NET tente de tronquer le cache d’objets et appelle régulièrement <xref:System.GC.Collect%2A?displayProperty=nameWithType> quand la limite en octets privés du processus est proche. Pour certaines applications, la fréquence des appels à <xref:System.GC.Collect%2A?displayProperty=nameWithType> ou la quantité de mémoire cache tronquée sont inefficaces. Les développeurs peuvent maintenant remplacer ou compléter le comportement par défaut en souscrivant des implémentations **IObserver** auprès du moniteur de mémoire de l’application.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) ajoute les fonctionnalités et les modifications suivantes :

**Possibilité de configurer les paramètres de sécurité de message par défaut avec TLS 1.1 ou TLS 1.2**

À compter de .NET Framework 4.7, WCF vous permet de configurer TSL 1.1 ou TLS 1.2 en plus de SSL 3.0 et TSL 1.0 en tant que protocole de sécurité de message par défaut. Il s’agit d’un paramètre à activer ; pour cela, vous devez ajouter l’entrée suivante à votre fichier de configuration d’application :

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**Amélioration de la fiabilité des applications WCF et de la sérialisation WCF**

WCF inclut plusieurs modifications du code qui éliminent la concurrence critique, améliorant ainsi les performances et la fiabilité des options de sérialisation. notamment :

- Meilleure prise en charge pour le mélange de code synchrone et asynchrone dans les appels à **SocketConnection.BeginRead** et à **SocketConnection.Read**.
- Meilleure fiabilité lors de l’abandon d’une connexion avec **SharedConnectionListener** et **DuplexChannelBinder**.
- Meilleure fiabilité des opérations de sérialisation lors de l’appel de la méthode <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType>.
- Meilleure fiabilité lors de la suppression d’un objet waiter en appelant la méthode **ChannelSynchronizer.RemoveWaiter**.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

Dans .NET Framework 4.7, Windows Forms améliore la prise en charge pour les moniteurs à haute résolution.

**Soutien DPI élevé**

À partir des applications qui ciblent .NET Framework 4.7, le .NET Framework prend en charge la haute résolution et la haute résolution dynamique pour les applications Windows Forms. La prise en charge de la haute résolution améliore la disposition et l’apparence des formulaires et des contrôles sur les moniteurs à haute résolution. La haute résolution dynamique change la disposition et l’apparence des formulaires et contrôles lorsque l’utilisateur modifie la haute résolution ou le facteur d’échelle d’affichage d’une application en cours d’exécution.

Le support DPI élevé est une fonction d’opt-in que vous configurez en définissant une [ \<section system.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) dans votre fichier de configuration d’application. Pour plus d’informations sur l’ajout de la prise en charge de la haute résolution et de la haute résolution dynamique à votre application Windows Forms, consultez [Prise en charge de la haute résolution dans Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Dans .NET Framework 4.7, WPF propose les améliorations suivantes :

**Prise en charge d’une pile tactile/de stylet basée sur les messages Windows WM_POINTER**

Vous pouvez désormais utiliser une fonction tactile ou stylet basée sur les [messages WM_POINTER](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages), au lieu de la plateforme WISP (Windows Ink Services Platform). Il s’agit d’une fonction d’opt-in dans .NET Framework. Pour plus d’informations, consultez la section [compatibilité de l’application.](../migration-guide/application-compatibility.md)

**Nouvelle implémentation pour l’impression d’API WPF**

Les API d’impression de WPF de la classe <xref:System.Printing.PrintQueue?displayProperty=nameWithType> appellent l’[API Print Document Package](/windows/desktop/printdocs/tailored-app-printing-api) de Windows au lieu de l’[API d’impression XPS](/windows/desktop/printdocs/xps-printing) dépréciée. Pour l’impact de cette modification sur la compatibilité d’application, consultez la section [compatibilité de l’application.](../migration-guide/application-compatibility.md)

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>Nouveautés de .NET Framework 4.6.2

Le .NET Framework 4.6.2 apporte de nouvelles fonctionnalités dans les domaines suivants :

- [ASP.NET](#ASPNET462)

- [Catégories de caractères](#Strings)

- [Chiffrement](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Convertir les formulaires Windows et les applications WPF en applications UWP](#UWPConvert)

- [Amélioration de débogage](#Debug462)

Pour obtenir la liste des nouvelles API ajoutées à .NET Framework 4.6.2, consultez la page [Changements au niveau des API de .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) sur GitHub. Pour obtenir la liste des fonctionnalités améliorées et des correctifs de bogues apportés à .NET Framework 4.6.2, consultez la page [Liste des changements de .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) sur GitHub. Pour plus d’informations, voir [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) dans le blog .NET.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

Dans le .NET Framework 4.6.2, ASP.NET propose les améliorations suivantes :

**Prise en charge améliorée des messages d’erreur localisés dans les validateurs d’annotation de données**

Les validateurs d’annotations de données vous permettent d’effectuer une validation en ajoutant un ou plusieurs attributs à une propriété de classe. L’élément <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> de l’attribut définit le texte du message d’erreur en cas d’échec de la validation. À compter du .NET Framework 4.6.2, ASP.NET facilite la localisation des messages d’erreur. Les messages d’erreur sont localisés si les conditions suivantes sont réunies :

1. L’élément <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> est fourni dans l’attribut de validation.

2. Le fichier de ressources est stocké dans le dossier App_LocalResources.

3. Le nom du fichier des ressources localisées a le `DataAnnotation.Localization.{` *nom*`}.resx`de formulaire , où le *nom* est un nom de culture dans le format *languageCode*`-`*pays/régionCode* ou *languageCode*.

4. Le nom de clé de la ressource est la chaîne assignée à l’attribut <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>, et sa valeur correspond au message d’erreur localisé.

Par exemple, l’attribut d’annotation de données suivant définit le message d’erreur de la culture par défaut pour une note non valide.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

Vous pouvez ensuite créer un fichier de ressources DataAnnotation.Localization.fr.resx, dont la clé est la chaîne de message d’erreur et dont la valeur est le message d’erreur localisé. Le fichier doit se trouver dans le dossier `App.LocalResources`. Par exemple, voici la clé et sa valeur dans un message d’erreur localisé en français (fr) :

| Nom                                 | Valeur                                     |
| ------------------------------------ | ----------------------------------------- |
| The rating must be between 1 and 10. | La note doit être comprise entre 1 et 10. |

 De plus, la localisation des annotations de données est extensible. Les développeurs peuvent incorporer leur propre fournisseur de localisation de chaînes en implémentant l’interface <xref:System.Web.Globalization.IStringLocalizerProvider> pour stocker la chaîne de localisation ailleurs que dans un fichier de ressources.

 **Prise en charge asynchrone avec les fournisseurs de magasins d’état de session**

 ASP.NET autorise désormais l’utilisation de méthodes retournant des tâches avec les fournisseurs de magasins d’état de session, ce qui permet ainsi aux applications ASP.NET de profiter de la scalabilité des opérations asynchrones. Pour prendre en charge les opérations asynchrones avec les fournisseurs de magasins d’état de session, ASP.NET propose une nouvelle interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, qui hérite de <xref:System.Web.IHttpModule> et permet aux développeurs d’implémenter leurs propres fournisseurs de modules d’état de session et de magasins de sessions asynchrones. L’interface se définit comme suit :

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 Par ailleurs, la classe <xref:System.Web.SessionState.SessionStateUtility> comporte deux nouvelles méthodes, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> et <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, qui peuvent être utilisées pour prendre en charge les opérations asynchrones.

 **Prise en charge asynchrone pour les fournisseurs de cache de sortie**

 À compter du .NET Framework 4.6.2, il est possible d’utiliser des méthodes qui retournent des tâches avec les fournisseurs de cache de sortie de façon à profiter de la scalabilité des opérations asynchrones.  Les fournisseurs qui implémentent ces méthodes réduisent le blocage de threads sur un serveur web et améliorent la scalabilité d’un service ASP.NET.

 Les API suivantes ont été ajoutées pour assurer la prise en charge des fournisseurs de cache de sortie asynchrones :

- La classe <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>, qui hérite de <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> et permet aux développeurs d’implémenter un fournisseur de cache de sortie asynchrone.

- La classe <xref:System.Web.Caching.OutputCacheUtility>, qui fournit les méthodes d’assistance pour configurer le cache de sortie.

- Les 18 nouvelles méthodes de la classe <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType>, à savoir : <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A> et <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- Les deux nouvelles méthodes de la classe <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> : <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> et <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- Les deux nouvelles méthodes de la classe <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> : <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> et <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- Les deux nouvelles méthodes de la classe <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> : <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> et <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- Dans la classe <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType>, la méthode <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A>.

- Dans la classe <xref:System.Web.Caching.CacheDependency>, la méthode <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A>.

<a name="Strings" />

### <a name="character-categories"></a>Catégories de caractères

Dans .NET Framework 4.6.2, les caractères sont classés en fonction de la [norme Unicode, version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). Dans le .NET Framework 4.6 et le .NET Framework 4.6.1, les caractères étaient classés en fonction des catégories de caractères Unicode 6.3.

La prise en charge d’Unicode 8.0 se limite à la classification des caractères de la classe <xref:System.Globalization.CharUnicodeInfo> et aux types et méthodes qui en dépendent. Il s’agit notamment de la classe <xref:System.Globalization.StringInfo>, de la méthode <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> surchargée et des [classes de caractères](../../standard/base-types/character-classes-in-regular-expressions.md) reconnues par le moteur d’expressions régulières du .NET Framework.  La comparaison et le tri des caractères et des chaînes ne sont pas affectés par cette évolution et continuent de s’appuyer sur le système d’exploitation sous-jacent ou bien, dans le cas des systèmes Windows 7, sur les données de caractères fournies par le .NET Framework.

Pour en savoir plus sur l’évolution des catégories de caractères entre Unicode 6.0 et Unicode 7.0, consultez l’article traitant de la [norme Unicode, version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) sur le site web du consortium Unicode. Pour en savoir plus sur les changements intervenus entre Unicode 7.0 et Unicode 8.0, consultez l’article traitant de la [norme Unicode, version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) sur le site web du consortium Unicode.

<a name="Crypto462" />

### <a name="cryptography"></a>Chiffrement

**Prise en charge des certificats X509 contenant l’algorithme DSA FIPS 186-3**

Le .NET Framework 4.6.2 ajoute la prise en charge des certificats X509 DSA(Digital Signature Algorithm) dont les clés dépassent la limite de 1 024 bits de la norme FIPS 186-2.

En plus de prendre en charge les clés plus volumineuses de FIPS 186-3, le .NET Framework 4.6.2 autorise le calcul de signatures à l’aide des algorithmes de hachage de la famille SHA-2 (SHA256, SHA384 et SHA512). La prise en charge de FIPS 186-3 est assurée par la nouvelle classe <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType>.

Dans la logique des récentes évolutions de la classe <xref:System.Security.Cryptography.RSA> de .NET Framework 4.6 et de la classe <xref:System.Security.Cryptography.ECDsa> de .NET Framework 4.6.1, la classe de base abstraite <xref:System.Security.Cryptography.DSA> de .NET Framework 4.6.2 propose des méthodes supplémentaires qui permettent aux appelants d’utiliser cette fonctionnalité sans opération de cast. Vous pouvez appeler la méthode d’extension <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> pour signer des données, comme le montre l’exemple suivant.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

Vous pouvez également appeler la méthode d’extension <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> pour vérifier les données signées, comme le montre l’exemple suivant.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

**Plus de clarté pour les entrées dans les routines de dérivation de clé ECDiffieHellman**

La prise en charge de l’accord d’échange de clés Curve Diffie-Hellman basé sur les courbes elliptiques avait été ajoutée à .NET Framework 3.5 avec trois routines de fonction de dérivation de clés (KDF) différentes. Les entrées à destination de ces routines, tout comme les routines proprement dites, étaient configurées via les propriétés de l’objet <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Mais comme les routines ne pouvaient pas toutes lire chaque propriété d’entrée, la confusion était de mise auprès des développeurs.

Pour résoudre ce problème dans .NET Framework 4.6.2, les trois méthodes suivantes ont été ajoutées à la classe de base <xref:System.Security.Cryptography.ECDiffieHellman> afin de représenter plus clairement ces routines KDF et leurs entrées :

|Méthode ECDiffieHellman|Description|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de la formule<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> où *x* représente le résultat du calcul de l’algorithme EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de la formule<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> où *x* représente le résultat du calcul de l’algorithme EC Diffie-Hellman.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de l’algorithme de dérivation de la fonction pseudo-aléatoire (PRF) TLS.|

**Prise en charge du chiffrement symétrique des clés persistantes**

La bibliothèque de chiffrement Windows (CNG) a ajouté la prise en charge du stockage de clés symétriques persistantes et de l’utilisation des clés symétriques stockées sur du matériel, et .NET Framework 4.6.2 a permis aux développeurs d’utiliser cette fonctionnalité.  Sachant que la notion de noms de clés et de fournisseurs de clés est spécifique à l’implémentation, cette fonctionnalité impose l’utilisation du constructeur des types d’implémentation concrets plutôt que l’approche par défaut privilégiée (comme l’appel de `Aes.Create`).

La prise en charge du chiffrement symétrique des clés persistantes existe pour les algorithmes AES (<xref:System.Security.Cryptography.AesCng>) et 3DES (<xref:System.Security.Cryptography.TripleDESCng>). Par exemple :

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

**Prise en charge de SignedXml pour le hachage SHA-2**

.NET Framework 4.6.2 ajoute une prise en charge à la classe <xref:System.Security.Cryptography.Xml.SignedXml> pour les méthodes de signature RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1, ainsi que pour les algorithmes Digest de référence SHA256, SHA384 et SHA512.

Les constantes d’URI sont toutes exposées dans <xref:System.Security.Cryptography.Xml.SignedXml> :

|Champ SignedXml|Constant|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Les programmes qui ont inscrit un gestionnaire <xref:System.Security.Cryptography.SignatureDescription> personnalisé dans <xref:System.Security.Cryptography.CryptoConfig> dans le but d’ajouter la prise en charge de ces algorithmes continueront de fonctionner comme par le passé. Cependant, comme il y a désormais les valeurs par défaut de la plateforme, l’inscription <xref:System.Security.Cryptography.CryptoConfig> n’est plus nécessaire.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

Le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) inclut les nouvelles fonctionnalités suivantes dans .NET Framework 4.6.2 :

**Regroupement de connexions et expirations de délai avec les bases de données Azure SQL**

Lorsque la mise en commun des connexions est activée et qu’un délai d’attente ou une autre erreur de connexion se produit, une exception est mise en cache, et l’exception mise en cache est lancée sur toute tentative de connexion ultérieure pour les 5 secondes à 1 minute suivantes. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

Ce comportement n’est pas souhaitable quand il s’agit d’établir des connexions à des bases de données Azure SQL Database, car les tentatives de connexion peuvent échouer avec des erreurs transitoires qui sont en général récupérées rapidement. Pour des nouvelles tentatives de connexion plus abouties, le comportement de période de blocage de pool de connexions est supprimé quand les connexions aux bases de données Azure SQL Database échouent.

L’ajout du `PoolBlockingPeriod` nouveau mot clé vous permet de sélectionner la période de blocage la mieux adaptée à votre application. Ces valeurs comprennent :

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

La période de blocage de pool de connexions d’une application qui se connecte à une base de données Azure SQL Database est désactivée, pendant que celle d’une application qui se connecte à une autre instance SQL Server est activée. Il s’agit de la valeur par défaut. Si le nom de point de terminaison d’un serveur se termine par l’un des éléments suivants, il est considéré comme une base de données Azure SQL Database :

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

La période de blocage de pool de connexion est toujours activée.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

La période de blocage de pool de connexion est toujours désactivée.

**Améliorations pour Always Encrypted**

SQLClient inaugure deux améliorations pour Always Encrypted :

- Pour améliorer les performances des requêtes paramétrables sur des colonnes de base de données chiffrées, les métadonnées de chiffrement sont désormais mises en cache pour les paramètres des requêtes. Dans la mesure où la propriété <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> est définie sur `true` (valeur par défaut), si une même requête est appelée plusieurs fois, le client ne récupère les métadonnées des paramètres qu’une seule fois sur le serveur.

- Les entrées de clés de chiffrement de colonnes présentes dans le cache de clés sont désormais supprimées au bout d’un délai configurable, qui est défini à l’aide de la propriété <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType>.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

Dans le .NET Framework 4.6.2, Windows Communication Foundation a été amélioré dans les domaines suivants :

**Prise en charge des certificats stockés à l’aide de CNG par la sécurité du transport WCF**

La sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG). Dans le .NET Framework 4.6.2, cette prise en charge se limite à l’utilisation de certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible le .NET Framework 4.6.2, cette fonctionnalité est activée par défaut.

Pour les applications qui ciblent le cadre .NET 4.6.1 et plus tôt, mais sont en cours d’exécution sur le cadre .NET 4.6.2, cette fonctionnalité peut être activée en ajoutant la ligne suivante à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section de l’app.config ou web.config fichier.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Vous pouvez en faire autant par programmation avec un code de ce type :

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**Meilleure prise en charge de plusieurs règles d’ajustement à l’heure d’été par la classe DataContractJsonSerializer**

Les clients peuvent utiliser un paramètre de configuration d’application pour déterminer si la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge plusieurs règles d’ajustement pour un même un fuseau horaire. Il est nécessaire d'accepter cette fonctionnalité. Pour l’activer, ajoutez le paramètre suivant à votre fichier app.config :

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Quand cette fonctionnalité est activée, un objet <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> utilise le type <xref:System.TimeZoneInfo> à la place du type <xref:System.TimeZone> pour désérialiser les données de date et d’heure. <xref:System.TimeZoneInfo> prend en charge plusieurs règles d’ajustement, ce qui permet d’utiliser des données de fuseau horaire historiques ; ce n’est pas le cas de <xref:System.TimeZone>.

Pour plus d’informations sur la structure <xref:System.TimeZoneInfo> et les ajustements de fuseau horaire, consultez [Vue d’ensemble des fuseaux horaires](../../standard/datetime/time-zone-overview.md).

**Meilleure correspondance NetNamedPipeBinding**

WCF propose un nouveau paramètre d’application qui peut être défini sur les applications clientes de telle sorte qu’elles se connectent systématiquement au service écoutant l’URI qui correspond le mieux à celui qu’elles demandent. Dans la mesure où ce paramètre d’application est défini sur `false` (valeur par défaut), les clients utilisant <xref:System.ServiceModel.NetNamedPipeBinding> peuvent tenter de se connecter à un service écoutant un URI qui est une sous-chaîne de l’URI demandé.

Par exemple, un client tente de se connecter à un service à l’écoute de `net.pipe://localhost/Service1`, mais un autre service de cet ordinateur s’exécutant avec des privilèges d’administrateur écoute `net.pipe://localhost`. Si ce paramètre d’application est défini sur `false`, le client tente de se connecter au mauvais service. Une fois le paramètre d’application défini sur `true`, le client se connecte systématiquement au service le plus approprié.

> [!NOTE]
> Les clients qui utilisent <xref:System.ServiceModel.NetNamedPipeBinding> recherchent les services à partir de leur adresse de base (s’ils en ont une) et non de l’adresse complète du point de terminaison. Pour faire en sorte que ce paramètre fonctionne toujours, le service doit utiliser une adresse de base unique.

Pour permettre cette modification, ajoutez le paramètre d’application suivant au fichier App.config ou Web.config de votre application cliente :

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3.0 n’est pas un protocole par défaut**

Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, SSL 3.0 n’est plus le protocole utilisé par défaut quand il s’agit de négocier une connexion sécurisée. Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 est inclus dans la liste de protocoles pour NetTcp. Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0. Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.

- La propriété <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>

- La propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>

- La [ \<](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section>de transport de la [ \<section>de netTcpBinding](../configure-apps/file-schema/wcf/nettcpbinding.md)

- La [ \<section sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) de la [ \<section customBinding>](../configure-apps/file-schema/wcf/custombinding.md)

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Dans le .NET Framework 4.6.2, Windows Presentation Foundation a été amélioré dans les domaines suivants :

**Tri des groupes**

Une application qui utilise un objet <xref:System.Windows.Data.CollectionView> pour regrouper les données peut désormais déclarer explicitement le mode de tri des groupes. Le tri explicite résout le problème du classement non intuitif qui se produit quand une application ajoute ou supprime dynamiquement des groupes ou quand elle modifie la valeur de propriétés d’élément impliquées dans le regroupement. Il peut aussi améliorer l’efficacité de la création de groupes en comparant les propriétés de regroupement non pas au niveau du tri de la collection complète mais du tri des groupes.

Pour prendre en charge le tri des groupes, les nouvelles propriétés <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> et <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> décrivent le mode de tri de la collection de groupes produite par l’objet <xref:System.ComponentModel.GroupDescription>. Ce comportement est analogue à la façon dont les propriétés <xref:System.Windows.Data.ListCollectionView> de même nom décrivent le mode de tri des éléments de données.

Il est possible d’utiliser les deux nouvelles propriétés statiques de la classe <xref:System.Windows.Data.PropertyGroupDescription>, <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> et <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, pour les cas les plus courants.

Par exemple, le code XAML suivant regroupe les données par âge, trie les groupes d’âge par ordre croissant, puis regroupe les éléments de chaque groupe d’âge par nom de famille.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

**Support clavier tactile**

Le support tactile permet le suivi de mise au point dans les applications WPF en invoquant et en rejetant automatiquement le clavier tactile dans Windows 10 lorsque l’entrée tactile est reçue par un contrôle qui peut prendre l’entrée textuelle.

Dans les versions précédentes de .NET Framework, les applications WPF ne peuvent pas opter pour le suivi de mise au point sans désactiver le support de styleT/geste tactile WPF. Par conséquent, les applications WPF doivent soit choisir la prise en charge complète des entrées tactiles WPF, soit privilégier la souris Windows.

**Résolution par moniteur**

Pour faire face à la prolifération récente des environnements à haute résolution et à résolution hybride pour les applications WPF, WPF dans le .NET Framework 4.6.2 autorise une prise en charge par moniteur. Pour savoir comment permettre à votre application WPF de prendre en charge la résolution par moniteur, consultez les [exemples et le guide du développeur](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) sur GitHub.

Dans les versions précédentes du .NET Framework, les applications WPF prennent en charge la résolution au niveau du système. En d’autres termes, l’interface utilisateur de l’application est éventuellement mise à l’échelle par le système d’exploitation, en fonction de la résolution du moniteur sur lequel l’application est affichée.

Pour les applications fonctionnant sous le cadre .NET 4.6.2, vous pouvez désactiver les modifications [ \<](../configure-apps/file-schema/runtime/runtime-element.md) DPI par moniteur dans les applications WPF en ajoutant une déclaration de configuration à la section>de votre fichier de configuration d’application, comme suit :

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

Dans le .NET Framework 4.6.2, Windows Workflow Foundation a été amélioré dans les domaines suivants :

**Soutien aux expressions et IntelliSense dans le Rehosted WF Designer**

À partir de .NET Framework 4.5, WF prend en charge les expressions de CMD dans le Visual Studio Designer et dans les flux de travail de code. Le Rehosted Workflow Designer est une caractéristique clé de WF qui permet au concepteur de workflow d’être dans une application en dehors de Visual Studio (par exemple, dans WPF).  Windows Workflow Foundation offre la possibilité de prendre en charge les expressions C et IntelliSense dans le Rehosted Workflow Designer. Pour plus d’informations, consultez le [blog Windows Workflow Foundation](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Dans les versions du cadre .NET avant 4.6.2, WF Designer IntelliSense est cassé quand un client reconstruit un projet de flux de travail de Visual Studio. Quand la génération du projet aboutit, les types de flux de travail ne se trouvent pas dans le concepteur, et IntelliSense affiche des avertissements dans la fenêtre **Liste d’erreurs** par rapport aux types de flux de travail manquants. .NET Framework 4.6.2 aborde ce problème et rend IntelliSense disponible.

**Les applications Workflow V1 pour lesquelles le suivi de flux de travail est activé s’exécutent désormais en mode FIPS**

Les ordinateurs pour lesquels le mode de conformité FIPS est activé peuvent désormais exécuter correctement une application de type Workflow version 1 en ayant le suivi de flux de travail activé. Pour permettre ce cas de figure, vous devez apporter la modification suivante à votre fichier app.config :

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Si ce scénario n’est pas autorisé, l’exécution de l’application continue de générer une exception avec le message « Cette implémentation ne fait pas partie des algorithmes de chiffrement validés FIPS pour les plateformes Windows ».

**Amélioration de flux de travail quand la mise à jour dynamique est utilisée avec le Concepteur de flux de travail Visual Studio**

Le Concepteur de flux de travail, le Concepteur d’activités d’organigramme et les autres Concepteurs d’activité de flux de travail peuvent désormais charger et afficher les flux de travail qui ont été enregistrés consécutivement à l’appel de la méthode <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>. Dans les versions du .NET Framework antérieures à .NET Framework 4.6.2, le fait de charger un fichier XAML dans Visual Studio pour un workflow enregistré après avoir appelé <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> peut occasionner les problèmes suivants :

- Le Concepteur de flux de travail ne peut pas charger le fichier XAML correctement (quand <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> est en fin de ligne).

- Le Concepteur d’activités d’organigramme ou les autres Concepteurs d’activités de flux de travail peuvent afficher tous les objets à leurs emplacements par défaut plutôt que les valeurs de propriétés jointes.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce a été mis à jour pour prendre en charge TLS 1.1 et TLS 1.2 en plus du protocole 1.0, qu’il prend déjà en charge. ClickOnce détecte automatiquement le protocole exigé ; aucune mesure supplémentaire n’est à prendre dans l’application ClickOnce pour activer la prise en charge de TLS 1.1 et 1.2.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Conversion des Windows Forms et des applications WPF en applications UWP

Windows permet désormais de porter les applications de bureau Windows, dont les applications WPF et Windows Forms, sur la plateforme Windows universelle (UWP). Cette technologie fait office de pont en vous permettant de migrer progressivement votre base de code existante vers UWP, et ainsi de porter votre application sur tous les appareils Windows 10.

Les applications de bureau converties obtiennent une identité d’application comparable à celle des applications UWP, ce qui rend les API UWP accessibles pour activer certaines fonctionnalités, telles que les vignettes dynamiques et les notifications. L’application continue de se comporter comme auparavant et s’exécute comme une application entièrement approuvée. Une fois l’application convertie, un processus de conteneur d’application peut être ajouté au processus d’approbation complète existant pour ajouter une interface utilisateur adaptative. Quand toutes les fonctionnalités sont déplacées vers le processus de conteneur d’application, le processus d’approbation complète peut être supprimé et la nouvelle application UWP peut être mise à la disposition de tous les appareils Windows 10.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Améliorations du débogage

L’*API de débogage non managée* a été améliorée dans .NET Framework 4.6.2 de façon à effectuer des analyses supplémentaires quand un <xref:System.NullReferenceException> est levé dans le but de permettre l’identification de la variable qui a la valeur `null` dans une même ligne de code source.   Pour favoriser ce scénario, les API ci-dessous ont été ajoutées à l’API de débogage non managé.

- Les interfaces [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md) et [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md), qui exposent les dossiers natifs des variables managées. Les débogueurs peuvent ainsi effectuer des analyses de flux de code quand une exception <xref:System.NullReferenceException> se produit et revenir en arrière pour identifier la variable managée qui correspond à l’emplacement natif qui avait la valeur `null`.

- La méthode [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) propose un mappage de ICorDebugType à [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), ce qui permet au débogueur d’obtenir un [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) sans instance de ICorDebugType. Les API existantes sur [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) peuvent ensuite servir à déterminer la disposition de classe du type.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>Nouveautés de .NET Framework 4.6.1

Le .NET Framework 4.6.1 apporte de nouvelles fonctionnalités dans les domaines suivants :

- [Chiffrement](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilage](#Profile461)

- [NGen](#NGEN461)

Pour plus d’informations sur .NET Framework 4.6.1, consultez les rubriques suivantes :

- [Liste des changements de .NET Framework 4.6.1](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [Compatibilité des applications dans la version 4.6.1](../migration-guide/application-compatibility.md)

- [Différences de l’API .NET Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (sur GitHub)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Chiffrement : prise en charge des certificats X509 contenant l’algorithme ECDSA

.NET Framework 4.6 a ajouté la prise en charge de l’algorithme RSACng pour les certificats X509. Le .NET Framework 4.6.1 ajoute la prise en charge des certificats X509 ECDSA (Elliptic Curve Digital Signature Algorithm).

ECDSA offre de meilleures performances et constitue un algorithme de chiffrement plus sécurisé que RSA. Il constitue un excellent choix quand les performances et la scalabilité de la sécurité de la couche de transport (TLS) constituent une préoccupation. L’implémentation du .NET Framework encapsule les appels dans les fonctionnalités Windows existantes.

L’exemple de code suivant montre combien il est facile de générer une signature pour un flux d’octets à l’aide de la nouvelle prise en charge des certificats X509 ECDSA inclus dans le .NET Framework 4.6.1.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Cela contraste fortement avec le code nécessaire pour générer une signature dans .NET Framework 4.6.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

Les éléments suivants ont été ajoutés à ADO.NET :

**Prise en charge de la fonctionnalité Chiffrement intégral pour les clés matérielles protégées**

ADO.NET prend désormais en charge le stockage des clés principales de colonnes Toujours chiffré en mode natif dans les modules de sécurité matériels (HSM, Hardware Security Modules). Cette prise en charge permet aux clients de tirer profit des clés asymétriques stockées dans les modules HSM sans avoir à écrire des fournisseurs de magasins de clés principales de colonnes personnalisés et sans les inscrire dans les applications.

Les clients doivent installer le fournisseur CSP fourni par le fabricant des modules HSM ou les fournisseurs de magasin de clés CNG sur les serveurs d’applications ou les ordinateurs clients pour accéder aux données Toujours chiffré protégées par des clés principales de colonnes stockées dans un module HSM.

**Amélioration <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> du comportement de connexion pour AlwaysOn**

Désormais, SqlClient fournit automatiquement une connexion plus rapide à un groupe de disponibilité AlwaysOn. Il détecte de façon transparente si votre application se connecte à un groupe de disponibilité AlwaysOn sur un autre sous-réseau, détecte rapidement le serveur actif actuel et fournit une connexion au serveur. Avant cette mise en production, une application devait définir la chaîne de connexion à inclure `"MultisubnetFailover=true"` pour indiquer qu’elle était connectée à un groupe de disponibilité AlwaysOn. Si le mot clé de connexion n’était pas défini sur `true`, une application pouvait rencontrer un dépassement du délai lors de la connexion à un groupe de disponibilité AlwaysOn. Avec cette version, une application *n’a plus* besoin de définir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> sur `true`. Pour plus d’informations sur la prise en charge de SqlClient pour les groupes de disponibilité AlwaysOn, consultez [Prise en charge de SqlClient pour la haute disponibilité et la récupération d’urgence](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation inclut un certain nombre d’améliorations et de modifications.

**performances améliorées**

Le retard de déclenchement d’événements tactiles a été résolu dans le .NET Framework 4.6.1. En outre, la saisie dans un contrôle <xref:System.Windows.Controls.RichTextBox> ne mobilise plus le thread de rendu pendant la saisie rapide.

**Améliorations de la vérification orthographique**

Le vérificateur orthographique de WPF a été mis à jour sur Windows 8.1 et les versions ultérieures pour tirer parti de la prise en charge, par le système d’exploitation, de la vérification orthographique de langues supplémentaires.  Aucune fonctionnalité n’a été modifiée sur les versions de Windows antérieures à Windows 8.1.

Comme dans les versions précédentes du .NET Framework, la langue d’un contrôle <xref:System.Windows.Controls.TextBox> ou d’un bloc <xref:System.Windows.Controls.RichTextBox> est détectée en recherchant des informations dans l’ordre suivant :

- `xml:lang`, le cas échéant.

- Langue d’entrée actuelle.

- Culture de thread actuelle.

Pour plus d’informations sur le support linguistique dans WPF, voir le [blog WPF sur .NET Framework 4.6.1 fonctionnalités](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).

**Prise en charge supplémentaire des dictionnaires personnalisés par utilisateur**

Dans le .NET Framework 4.6.1, WPF reconnaît les dictionnaires personnalisés qui sont inscrits de manière globale. Cette fonctionnalité est disponible en plus de la possibilité de les inscrire par contrôle.

Dans les versions précédentes de WPF, les dictionnaires personnalisés ne reconnaissaient pas les listes Mots exclus et Correction automatique. Ils sont pris en charge sur Windows 8.1 et Windows 10 via l’utilisation de fichiers qui peuvent être placés sous le répertoire `%AppData%\Microsoft\Spelling\<language tag>`.  Les règles suivantes s’appliquent à ces fichiers :

- Les fichiers doivent avoir l’extension .dic (pour les mots ajoutés), .exc (pour les mots exclus) ou .acl (pour la correction automatique).

- Les fichiers doivent être en texte brut UTF-16 LE qui commence par la marque d’ordre d’octet.

- Chaque ligne doit comporter un mot (dans les listes de mots ajoutés et exclus) ou une paire de corrections automatiques avec les mots séparés par une barre verticale (« &#124; ») (dans la liste de mots Correction automatique).

- Ces fichiers sont considérés en lecture seule et ne sont pas modifiés par le système.

> [!NOTE]
> Ces nouveaux formats de fichier ne sont pas directement pris en charge par les API de correction orthographique WPF, et les dictionnaires personnalisés fournis à WPF dans les applications doivent continuer à utiliser les fichiers .lex.

**Exemples**

Vous trouverez des exemples WPF dans le dépôt GitHub [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples). Aidez-nous à améliorer nos exemples en nous envoyant une requête d’extraction ou en ouvrant un [problème GitHub](https://github.com/Microsoft/WPF-Samples/issues).

**Extensions DirectX**

WPF inclut un [package NuGet](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) qui fournit de nouvelles implémentations de <xref:System.Windows.Interop.D3DImage> facilitant l’interaction avec du contenu DX10 et Dx11. Le code de ce package a été mis en open source et est disponible [sur GitHub](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation : Transactions

La méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> peut maintenant utiliser un gestionnaire de transactions distribuées autre que MSDTC pour promouvoir la transaction. Pour ce faire, spécifiez un identificateur de promoteur de transaction GUID pour la nouvelle surcharge <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType>. Si cette opération réussit, des limitations sont placées sur les fonctionnalités de la transaction. Une fois qu’un promoteur de transaction non MSDTC est inscrit, les méthodes suivantes lèvent un <xref:System.Transactions.TransactionPromotionException>, car elles requièrent une promotion vers MSDTC :

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

Une fois qu’un promoteur de transaction non MSDTC est inscrit, il doit être utilisé pour les futures inscriptions durables en utilisant les protocoles qu’il définit. Vous pouvez obtenir le <xref:System.Guid> du promoteur de transaction à l’aide de la propriété <xref:System.Transactions.Transaction.PromoterType%2A>. Lorsque la transaction est promue, le promoteur de transaction fournit un tableau d’octets (<xref:System.Byte> qui représente le jeton promu. Une application peut obtenir le jeton promu pour une transaction non MSDTC promue à l’aide de la méthode <xref:System.Transactions.Transaction.GetPromotedToken%2A>.

Les utilisateurs de la nouvelle surcharge <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> doit suivre une séquence d’appel spécifique pour que l’opération de promotion se termine correctement. Ces règles sont documentées dans la documentation de la méthode.

<a name="Profile461" />

### <a name="profiling"></a>Profilage

L’API de profilage non managée a été améliorée comme suit :

- Meilleure prise en charge de l’accès aux fichiers PDB dans l’interface [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md).

  Dans ASP.NET Core, la compilation des assemblys en mémoire par Roslyn est beaucoup plus courante. Pour les développeurs qui créent des outils de profilage, cela signifie que les fichiers PDB qui étaient historiquement sérialisés sur le disque risquent de ne plus être présents. Les outils de profilage utilisent souvent des fichiers PDB pour remapper du code aux lignes sources pour des tâches telles que la couverture du code ou l’analyse des performances ligne par ligne. L’interface [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) inclut désormais deux nouvelles méthodes, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) et [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), qui permettent de fournir ces outils de profilage avec un accès aux données PDB en mémoire. En utilisant les nouvelles API, un profileur peut obtenir le contenu d’un fichier PDB en mémoire sous la forme d’un tableau d’octets, puis le traiter ou le sérialiser sur le disque.

- Meilleure instrumentation avec l’interface ICorProfiler.

  Les profileurs qui utilisent la fonctionnalité ReJit des API `ICorProfiler` pour l’instrumentation dynamique peuvent maintenant modifier certaines métadonnées. Précédemment, ces outils pouvaient instrumenter le langage intermédiaire à tout moment, mais les métadonnées ne pouvaient être modifiées qu’au moment du chargement du module. Étant donné que le langage intermédiaire fait référence aux métadonnées, cela limitait les types d’instrumentation qui pouvaient être effectuées. Nous avons levé certaines de ces limites en ajoutant la méthode [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) méthode pour prendre en charge `AssemblyRef` `TypeRef`un `TypeSpec` `MemberRef`sous-ensemble de modifications de métadonnées après les charges du module, en particulier en ajoutant de nouvelles , , , `MemberSpec`et `UserString` les enregistrements. Cette modification permet une plus large gamme d’instrumentations instantanées possibles.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Fichiers PDB du générateur d’images natives (NGen)

Le suivi d’événements entre ordinateurs permet aux clients de profiler un programme sur l’Ordinateur A et d’examiner les données de profilage avec le mappage des lignes sources sur l’Ordinateur B. Avec les versions antérieures du .NET Framework, l’utilisateur devait copier tous les modules et les images natives de l’ordinateur profilé vers l’ordinateur d’analyse qui contenait le fichier PDB en langage intermédiaire pour créer le mappage du code source au code natif. Ce processus peut fonctionner correctement lorsque les fichiers sont relativement petits, comme pour les applications de téléphone. Toutefois, les fichiers peuvent être très volumineux sur des systèmes de bureau et leur copie peut prendre beaucoup de temps.

Avec les fichiers PDB de NGen, NGen peut créer un fichier PDB qui contient le mappage du langage intermédiaire au code natif sans dépendance sur le fichier PDB en langage intermédiaire. Dans notre scénario de suivi d’événements entre ordinateurs, il suffit de copier le fichier PDB de l’image native généré par l’Ordinateur A sur l’Ordinateur B et d’utiliser les [API Debug Interface Access](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) pour lire le mappage du code source au code en langage intermédiaire du fichier PDB en langage intermédiaire et le mappage du code en langage intermédiaire au code natif du fichier PDB de l’image native. La combinaison des deux mappages fournit un mappage du code source au code natif. Étant donné que le fichier PDB de l’image native est beaucoup plus petit que l’ensemble des modules et images natives, le processus de copie de l’Ordinateur A vers l’Ordinateur B est beaucoup plus rapide.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>Nouveautés du .NET 2015

Le .NET Framework 2015 introduit le .NET Framework 4.6 et le .NET Core. Certaines nouvelles fonctionnalités s'appliquent aux deux infrastructures, alors que d'autres sont spécifiques au .NET Framework 4.6 ou au .NET Core.

- **ASP.NET Core**

  .NET 2015 inclut ASP.NET Core, qui est une implémentation .NET pour la création d’applications cloud modernes. ASP.NET Core est modulable, ce qui vous permet d’inclure uniquement les fonctionnalités nécessaires dans votre application. Elle peut être hébergée sur IIS ou auto-hébergée dans un processus personnalisé. Par ailleurs, vous pouvez exécuter les applications avec différentes versions du .NET Framework sur le même serveur. Elle inclut un nouveau système de configuration d'environnement conçu pour le déploiement cloud.

  MVC, les API web et les pages web sont unifiés dans une infrastructure unique appelée MVC 6. Vous créez des applications ASP.NET Core via les outils de Visual Studio 2015 ou ultérieur. Vos applications existantes fonctionneront sur le nouveau .NET Framework. Toutefois, pour générer une application qui utilise MVC 6 ou SignalR 3, vous devez utiliser le système de projet de Visual Studio 2015 ou ultérieur.

  Pour plus d’informations, consultez [ASP.NET Core](/aspnet/core/).

- **Mises à jour d’ASP.NET**

  - **API basée sur des tâches pour le vidage de réponse asynchrone**

    ASP.NET fournit désormais une API simple basée sur des tâches pour le vidage de réponse asynchrone, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, qui autorise les réponses à être vidées de façon asynchrone à l'aide du support `async/await` de votre langue.

  - **La liaison de modèle prend en charge les méthodes qui retournent des tâches**

    Dans le .NET Framework 4.5, ASP.NET a ajouté une fonctionnalité de liaison de modèle qui autorise une approche extensible, axée sur le code pour les opérations de données CRUD dans les contrôles utilisateur et les pages Web Forms. Le système de liaison de modèle prend désormais en charge les méthodes de liaison de modèle avec renvoi de <xref:System.Threading.Tasks.Task>. Cette fonctionnalité permet aux développeurs de Web Forms d'obtenir les avantages de la scalabilité du modèle asynchrone et la simplicité du système de liaison de données lorsqu'ils utilisent les versions plus récentes des ORM, y compris l'Entity Framework.

    La liaison de modèle asynchrone est contrôlée par le paramètre de configuration `aspnet:EnableAsyncModelBinding`.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    Sur les applications qui ciblent le .NET Framework 4.6, sa valeur par défaut est `true`. Sur les applications s'exécutant sur le .NET Framework 4.6 qui ciblent une version antérieure du .NET Framework, sa valeur par défaut est `false`. Son activation s'obtient en définissant le paramètre de configuration avec la valeur `true`.

  - **Prise en charge de HTTP/2 (Windows 10)**

    [HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) est une nouvelle version du protocole HTTP qui offre une bien meilleure utilisation de la connexion (moins d’allers-retours entre le client et le serveur), ce qui réduit la latence pendant le chargement des pages web pour les utilisateurs.  Ce sont les pages web (par opposition aux services) qui profitent le plus de HTTP/2, car le protocole optimise les demandes de plusieurs artefacts dans une expérience unique. La prise en charge de HTTP/2 a été ajoutée à ASP.NET dans .NET Framework 4.6. Étant donné que les fonctionnalités réseau existent sur plusieurs couches, de nouvelles fonctionnalités ont dû être rajoutées dans Windows, IIS et ASP.NET pour activer HTTP/2. Vous devez exécuter Windows 10 pour utiliser HTTP/2 avec ASP.NET.

    HTTP/2 est également pris en charge et activé par défaut sur les applications UWP Windows 10 qui utilisent l'API <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>.

    Afin de fournir un moyen d’utiliser la fonctionnalité [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) dans les applications ASP.NET, une nouvelle méthode avec deux surcharges, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> et <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, a été ajoutée à la classe <xref:System.Web.HttpResponse>.

    > [!NOTE]
    > Alors qu’ASP.NET Core prend en charge HTTP/2, la prise en charge de la fonctionnalité PUSH PROMISE n’a pas encore été ajoutée.

    Le navigateur et le serveur web (IIS sur Windows) effectuent tout le travail. Vous n'avez pas de tâches lourdes à effectuer pour vos utilisateurs.

    La plupart des [principaux navigateurs prennent en charge HTTP/2](https://www.wikipedia.org/wiki/HTTP/2). Il est donc probable que vos utilisateurs bénéficient de la prise en charge de HTTP/2 si tel est le cas de votre serveur.

  - **Prise en charge du protocole de liaison de jeton**

    Microsoft et Google ont travaillé en collaboration sur une nouvelle approche de l’authentification, appelée le [Protocole de liaison de jeton](https://github.com/TokenBinding/Internet-Drafts). La prémisse est que les jetons d’authentification (dans votre cache de navigateur) peuvent être volés et utilisés par les criminels pour accéder à des ressources autrement sécurisées (par exemple, votre compte bancaire) sans exiger votre mot de passe ou toute autre connaissance privilégiée. Le nouveau protocole vise à contenir ce problème.

    Le protocole de liaison de jeton sera implémenté dans Windows 10 en tant que fonctionnalité du navigateur. Les applications ASP.NET participeront au protocole, en validant les jetons d'authentification pour qu'ils soient légitimes. Les implémentations côté client et serveur établissent la protection de bout en bout spécifiée par le protocole.

  - **Algorithmes de hachage de chaîne aléatoire**

    .NET Framework 4.5 a introduit un [algorithme de hachage de chaîne aléatoire](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Cependant, il n'est pas pris en charge par ASP.NET en raison de certaines fonctionnalités ASP.NET fondées sur un code de hachage stable. Dans le .NET Framework 4.6, les algorithmes de hachage de chaîne aléatoire sont désormais pris en charge. Pour activer cette fonctionnalité, utilisez le paramètre de configuration `aspnet:UseRandomizedStringHashAlgorithm`.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  ADO .NET prend désormais en charge la fonctionnalité Toujours chiffré disponible dans SQL Server 2016 version préliminaire CTP2 (Community Technology Preview 2). Grâce à Always Encrypted, SQL Server peut effectuer des opérations sur des données chiffrées. Qui plus est, la clé de chiffrement réside avec l’application à l’intérieur de l’environnement approuvé du client, et non sur le serveur. Always Encrypted sécurise les données client pour que les administrateurs de base de données n’aient pas accès aux données en texte brut. Le chiffrement et le déchiffrement de données se produit de manière transparente au niveau du pilote, ce qui réduit des modifications à apporter aux applications existantes. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) et [Always Encrypted (développement client)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **Compilateur JIT 64 bits pour le code managé**

  .NET Framework 4.6 propose une nouvelle version du compilateur JIT 64 bits (anciennement RyuJIT). Le nouveau compilateur 64 bits offre des améliorations significatives des performances par rapport à l'ancien compilateur JIT 64 bits. Le nouveau compilateur 64 bits est activé pour les processus 64 bits qui s’exécutent au-dessus de .NET Framework 4.6. Votre application s'exécute dans un processus 64 bits s'il est compilé en mode 64 bits ou AnyCPU, et s'exécute sur un système d'exploitation 64 bits. Bien que toutes les mesures nécessaires aient été prises pour que la transition vers le nouveau compilateur soit aussi transparente que possible, des modifications du comportement sont possibles.

  Le nouveau compilateur JIT 64 bits inclut également des fonctionnalités d'accélération matérielle SIMD en cas d'association aux types SIMD de l'espace de noms <xref:System.Numerics>, ce qui peut produire une bonne amélioration des performances.

- **Améliorations du chargeur d’assembly**

  Le chargeur d'assembly utilise désormais la mémoire plus efficacement en déchargeant les assemblys IL après le chargement d'une image NGEN correspondante. Cette modification réduit la mémoire virtuelle, ce qui est particulièrement utile pour les grandes applications 32 bits (tels que Visual Studio), et économise aussi la mémoire physique.

- **Changements des bibliothèques de classes de base**

  Plusieurs nouvelles API ont été ajoutées au .NET Framework 4.6 pour des scénarios clés. Vous remarquerez les changements et les ajouts suivants :

  - **Implémentations d’IReadOnlyCollection\<T>**

    Des collections supplémentaires implémentent <xref:System.Collections.Generic.IReadOnlyCollection%601>, comme <xref:System.Collections.Generic.Queue%601> et <xref:System.Collections.Generic.Stack%601>.

  - **CultureInfo.CurrentCulture et CultureInfo.CurrentUICulture**

    Les propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> sont désormais en lecture et en écriture, et non plus en lecture seule. Si vous affectez un nouvel objet <xref:System.Globalization.CultureInfo> à ces propriétés, la culture du thread actuel définie par la propriété `Thread.CurrentThread.CurrentCulture` et la culture du thread d'interface utilisateur actuel définie par les propriétés `Thread.CurrentThread.CurrentUICulture` changent également.

  - **Améliorations du nettoyage de la mémoire (GC)**

    La classe <xref:System.GC> inclut désormais les méthodes <xref:System.GC.TryStartNoGCRegion%2A> et <xref:System.GC.EndNoGCRegion%2A>, qui vous permettent d'interdire le garbage collection durant l'exécution d'un chemin critique.

    Une nouvelle surcharge de la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> vous permet de contrôler si le tas de petits objets et le tas d'objets volumineux sont rangés et compactés, ou rangés uniquement.

  - **Types SIMD**

    L'espace de noms <xref:System.Numerics> inclut désormais un certain nombre de types SIMD, tels que <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>.

    Comme le nouveau compilateur JIT 64 bits inclut également des fonctionnalités d'accélération matérielle SIMD, il en découle une amélioration des performances particulièrement significative lorsque vous utilisez les types SIMD avec le nouveau compilateur JIT 64 bits.

  - **Mises à jour du chiffrement**

    L’API <xref:System.Security.Cryptography?displayProperty=nameWithType> est mise à jour pour prendre en charge les [API de chiffrement CNG de Windows](/windows/desktop/SecCNG/cng-reference). Jusqu’à présent, le .NET Framework reposait entièrement sur une [version antérieure des API de chiffrement Windows](/windows/desktop/SecCrypto/cryptography-portal) comme base d’implémentation de <xref:System.Security.Cryptography?displayProperty=nameWithType>. Nous avons reçu des demandes pour la prise en charge de l’API CNG, car elle prend en charge les [algorithmes de chiffrement modernes](/windows/desktop/SecCNG/cng-features#suite-b-support), qui sont importants pour certaines catégories d’applications.

    .NET Framework 4.6 inclut les améliorations suivantes pour prendre en charge l’API de chiffrement CNG de Windows :

    - Un ensemble de méthodes d'extension pour les certificats X509, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` et `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, qui retourne une implémentation CNG plutôt qu'une implémentation CAPI lorsque cela est possible. (Certaines cartes à puce, etc., nécessitent toujours CAPI, et les API gèrent le secours).

    - La classe <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>, qui fournit une implémentation CNG de l'algorithme RSA.

    - Améliorations apportées à l'API RSA afin que les opérations courantes ne nécessitent plus de conversion. Par exemple, le chiffrement des données utilisant un objet <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nécessite un code comme celui qui suit dans les versions antérieures du .NET Framework.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      Le code qui utilise les nouvelles API de chiffrement dans .NET Framework 4.6 peut être réécrit comme suit pour éviter la conversion.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Prise en charge de la conversion des dates et heures vers ou à partir de Unix**

    Les nouvelles méthodes suivantes ont été ajoutées à la structure <xref:System.DateTimeOffset> pour prendre en charge la conversion des valeurs de date et d'heure vers ou depuis Unix :

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Commutateurs de compatibilité**

    La <xref:System.AppContext> classe ajoute une nouvelle fonctionnalité de compatibilité qui permet aux rédacteurs de bibliothèques de fournir un mécanisme uniforme d’opt-out pour de nouvelles fonctionnalités pour leurs utilisateurs. Il établit un contrat vaguement couplé entre les composants afin de communiquer une demande d’opt-out. Cette fonctionnalité est particulièrement importante quand une modification est apportée aux fonctionnalités existantes. À l'inverse, il existe déjà une activation implicite des nouvelles fonctionnalités.

    Avec <xref:System.AppContext>, les bibliothèques définissent et exposent des commutateurs de compatibilité, tandis que le code qui en dépend peut définir ces commutateurs pour qu'ils aient un impact sur le comportement de la bibliothèque. Par défaut, les bibliothèques fournissent la nouvelle fonctionnalité et ne peuvent la modifier (c'est-à-dire fournir la version antérieure) que si le commutateur est défini.

    Une application (ou une bibliothèque) peut déclarer la valeur d'un commutateur (qui est toujours une valeur <xref:System.Boolean>) définie par une bibliothèque dépendante. Le commutateur a toujours implicitement la valeur `false`. En définissant le commutateur avec la valeur `true`, vous l'activez. En définissant explicitement le commutateur avec la valeur `false`, vous obtenez le nouveau comportement.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    La bibliothèque doit vérifier si un consommateur a déclaré la valeur du commutateur et s'il l'utilise ensuite correctement.

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    Il est préférable d'utiliser un format homogène pour les commutateurs, car ils constituent un contrat formel exposé par une bibliothèque. Voici les deux formats évidents.

    - *Commutateur*.*espace de noms*.*nom_commutateur*

    - *Commutateur*.*bibliothèque*.*nom_commutateur*

  - **Changements apportés au modèle asynchrone basé sur les tâches (TAP)**

    Pour les applications qui ciblent le .NET Framework 4.6, les objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> héritent de la culture et de la culture d’interface utilisateur du thread appelant. Le comportement des applications qui ciblent les versions antérieures du .NET Framework, ou qui ne ciblent pas une version spécifique du .NET Framework n'est pas affecté. Pour plus d'informations, consultez la section « Culture et opérations asynchrones basées sur les tâches » de la rubrique relative à la classe <xref:System.Globalization.CultureInfo>.

    La classe <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> permet de représenter les données ambiantes locales à un flux de contrôle asynchrone donné, par exemple une méthode `async`. Elle peut être utilisée pour conserver les données entre plusieurs threads. Vous pouvez également définir une méthode de rappel qui est avertie chaque fois que les données ambiantes changent, soit parce que la propriété <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> a été modifiée explicitement, soit parce que le thread a rencontré une transition de contexte.

    Trois méthodes pratiques, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, ont été ajoutées au modèle asynchrone basé sur des tâches (TAP) pour retourner les tâches terminées dans un état particulier.

    La classe <xref:System.IO.Pipes.NamedPipeClientStream> prend désormais en charge la communication asynchrone avec sa nouvelle méthode <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> .

  - **EventSource prend désormais en charge l’écriture dans le journal des événements**

    Vous pouvez maintenant utiliser la classe <xref:System.Diagnostics.Tracing.EventSource> pour enregistrer les messages administratifs ou opérationnels dans le journal des événements, en plus des sessions ETW existantes créées sur l'ordinateur. Par le passé, vous deviez utiliser le package Microsoft.Diagnostics.Tracing.EventSource NuGet pour cette fonctionnalité. Cette fonctionnalité est désormais intégrée à .NET Framework 4.6.

    Le package NuGet et .NET Framework 4.6 ont tous deux été mis à jour avec les fonctionnalités suivantes :

    - **Événements dynamiques**

      Permet que les événements soient définis « à la volée », sans créer de méthodes d'événement.

    - **Charges utiles enrichies**

      Permet que les tableaux et les classes avec attributs spécifiques, ainsi que les types primitifs, soient transmis comme charge utile

    - **Suivi des activités**

      Tous les événements entre les événements de début et de fin sont marqués avec un ID qui représente toutes les activités en cours.

    Pour prendre en charge ces fonctionnalités, la méthode <xref:System.Diagnostics.Tracing.EventSource.Write%2A> surchargée a été ajoutée à la classe <xref:System.Diagnostics.Tracing.EventSource>.

- **Windows Presentation Foundation (WPF)**

  - **Améliorations HDPI**

    La prise en charge HDPI dans WPF est désormais mieux assurée dans le .NET Framework 4.6. Des améliorations ont été apportées à l'arrondi de disposition pour réduire les instances de découpage dans les contrôles avec bordures. Par défaut, cette fonctionnalité est activée uniquement si votre <xref:System.Runtime.Versioning.TargetFrameworkAttribute> a la valeur .NET 4.6.  Les applications qui ciblent les versions antérieures du cadre, mais sont en cours d’exécution sur le cadre .NET 4.6 peuvent opter pour le nouveau comportement en ajoutant la ligne suivante à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier app.config:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    Les fenêtres WPF chevauchant plusieurs écrans avec différents paramètres DPI (programme d'installation multi-DPI) sont à présent restituées entièrement sans zones obscurcies. Vous pouvez désactiver ce comportement en ajoutant la ligne suivante à la section `<appSettings>` du fichier app.config :

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    La prise en charge du chargement automatique du curseur approprié selon le paramètre DPI a été ajoutée à <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

  - **Meilleure interaction tactile**

    Les rapports de clients sur [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) selon lesquels l’interaction tactile produisait un comportement imprévisible ont été traités dans le .NET Framework 4.6. Le seuil de double appui pour les applications du Windows Store et les applications WPF est maintenant le même que dans Windows 8.1 et versions ultérieures.

  - **Prise en charge transparente des fenêtres enfants**

    WPF dans le .NET Framework 4.6. prend en charge les fenêtres enfants transparentes dans Windows 8.1 et versions ultérieures. Cela vous permet de créer des fenêtres enfants non rectangulaires et transparentes dans vos fenêtres de niveau supérieur. Vous pouvez désactiver cette fonctionnalité en affectant à la propriété <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> la valeur `true`.

- **Fondation De communication Windows (WCF)**

  - **Prise en charge SSL**

    WCF prend désormais en charge la version TLS 1.1 et TLS 1.2 de SSL, en plus de SSL 3.0 et TLS 1.0, lorsque vous utilisez NetTcp avec l'authentification client et la sécurité de transport. Il est désormais possible de sélectionner le protocole à utiliser, ou de désactiver les anciens protocoles moins sécurisés. Cela peut être effectué en définissant la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> ou en ajoutant le code suivant à un fichier de configuration.

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - **Envoi de messages à l’aide de différentes connexions HTTP**

    WCF permet désormais aux utilisateurs de s'assurer que certains messages sont envoyés à l'aide de différentes connexions HTTP sous-jacentes. Il existe deux façons d'effectuer cette opération :

    - **Utilisation d’un préfixe de nom de groupe de connexion**

      Les utilisateurs peuvent spécifier une chaîne que WCF utilisera comme préfixe du nom de groupe de connexion. Deux messages avec des préfixes différents sont envoyés à l'aide de différentes connexions HTTP sous-jacentes. Vous définissez le préfixe en ajoutant une paire clé/valeur à la propriété <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> du message. La clé est « HttpTransportConnectionGroupNamePrefix » ; la valeur est le préfixe souhaité.

    - **Utilisation de différentes fabriques de canaux**

      Les utilisateurs peuvent aussi activer une fonctionnalité qui permet de s'assurer que les messages envoyés à l'aide de canaux créés par différentes fabriques de canaux utilisent différentes connexions HTTP sous-jacentes. Pour activer cette fonctionnalité, les utilisateurs doivent définir la propriété `appSetting` suivante avec la valeur `true` :

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Windows Workflow Foundation (WWF)**

  Vous pouvez maintenant spécifier le nombre de secondes pendant lesquelles un service de workflow maintient une demande d'opération exceptionnelle quand il existe un signet « non-protocole » en attente avant l'expiration de la demande. Un signet « non-protocole » est un signet qui n'est pas lié à des activités de réception en attente. Comme certaines activités créent des signets non-protocole dans leur implémentation, il peut ne pas être évident qu'un signet non-protocole existe. Ceux-ci incluent État et Prélèvement. Par conséquent, si vous avez un service de workflow mis en œuvre avec une machine à états ou contenant une activité de prélèvement, vous aurez probablement des signets non-protocole. Vous spécifiez l'intervalle en ajoutant la ligne suivante à la section `appSettings` de votre fichier app.config :

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  La valeur par défaut est 60 secondes. Si `value` a la valeur 0, les demandes exceptionnelles sont immédiatement rejetées comme erreur avec un texte tel que le suivant :

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  C'est le même message que vous recevez en cas d'opération exceptionnelle et d'absence de signet non-protocole.

  Si la valeur de l'élément `FilterResumeTimeoutInSeconds` est différente de zéro, il existe des signets non-protocole, l'intervalle de délai d'attente expire et l'opération échoue avec un message d'expiration.

- **Transactions**

  Vous pouvez maintenant inclure l'identificateur de transaction distribuée pour la transaction ayant provoqué la levée d'une exception dérivée de <xref:System.Transactions.TransactionException>. Pour ce faire, ajoutez la clé suivante à la section `appSettings` de votre fichier app.config :

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  La valeur par défaut est `false`.

- **Mise en réseau**

  - **Réutilisation de socket**

    Windows 10 inclut un nouvel algorithme de mise en réseau à haute scalabilité qui améliore l'utilisation des ressources de l'ordinateur en réutilisant les ports locaux pour les connexions TCP sortantes. .NET Framework 4.6 prend en charge le nouvel algorithme, permettant aux applications .NET de tirer parti du nouveau comportement. Dans les précédentes versions de Windows, il y avait une limite artificielle de connexions simultanées (généralement 16 384, taille par défaut de la plage de ports dynamiques), ce qui pouvait limiter la scalabilité d'un service en provoquant l'épuisement du port sous charge.

    Dans le cadre .NET 4.6, deux API ont été ajoutées pour permettre la réutilisation portuaire, ce qui supprime efficacement la limite de 64 KB sur les connexions simultanées :

    - Valeur de l'énumération <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>.

    - La propriété <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>.

    Par défaut, la propriété <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> est `false` sauf si la valeur `HWRPortReuseOnSocketBind` de la clé de Registre `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` est définie sur 0x1. Pour activer la réutilisation de port local sur les connexions HTTP, définissez la propriété <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> avec la valeur `true`. Toutes les connexions de socket TCP sortantes de <xref:System.Net.Http.HttpClient> et <xref:System.Net.HttpWebRequest> sont alors contraintes d’utiliser une nouvelle option de socket Windows 10, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), qui permet la réutilisation du port local.

    Les développeurs écrivant une application de sockets uniquement peuvent spécifier l'option <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> lors de l'appel d'une méthode telle que <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> afin que les sockets sortants réutilisent les ports locaux lors de la liaison.

  - **Prise en charge des noms de domaine internationaux et PunyCode**

    Une nouvelle propriété, <xref:System.Uri.IdnHost%2A>, a été ajoutée à la classe <xref:System.Uri> pour mieux prendre en charge les noms de domaine internationaux et PunyCode.

- **Redimensionnement dans les contrôles Windows Forms**

  Cette fonctionnalité a été développée dans .NET Framework 4.6 pour inclure les types <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.ToolStripSplitButton>, ainsi que le rectangle spécifié par la propriété <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> utilisée durant le dessin de <xref:System.Drawing.Design.UITypeEditor>.

  Il est nécessaire d'accepter cette fonctionnalité. Pour l'activer, affectez à l'élément `EnableWindowsFormsHighDpiAutoResizing` la valeur `true` dans le fichier de configuration de l'application (app.config) :

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Prise en charge des encodages de pages de codes**

  .NET Core prend en charge principalement les codages Unicode, et fournit par défaut une prise en charge limitée des codages de pages de codes. Vous pouvez ajouter la prise en charge des encodages de pages de codes disponibles dans .NET Framework, mais non pris en charge dans .NET Core, en inscrivant les encodages de pages de codes avec la méthode <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  Les applications Windows pour Windows 10 qui ciblent le .NET Core et sont écrites en C# ou Visual Basic peuvent désormais tirer parti d'une nouvelle technologie qui compile les applications en code natif plutôt qu'en code IL (Intermediate Language). Il en résulte des applications caractérisées par un démarrage plus rapide et un temps d'exécution accéléré. Pour plus d’informations, consultez [Compilation d’applications avec .NET Native](../net-native/index.md). Pour obtenir une vue d’ensemble de .NET Native illustrant sa différence par rapport à la compilation JIT et NGEN, et pour connaître ses implications au niveau de votre code, consultez [Compilation et .NET Native](../net-native/net-native-and-compilation.md).

  Vos applications sont compilées en code natif par défaut dans Visual Studio 2015 ou ultérieur. Pour plus d’informations, consultez [Prise en main de .NET Native](../net-native/getting-started-with-net-native.md).

  Pour permettre la prise en charge du débogage des applications .NET Native, un certain nombre de nouvelles interfaces et d'énumérations ont été ajoutées à l'API de débogage non managée. Pour plus d’informations, consultez la rubrique [Débogage (Référence des API non managées)](../unmanaged-api/debugging/index.md).

- **Packages du .NET Framework open source**

  .NET Core paquets tels que les collections immuables, [API SIMD](https://www.nuget.org/packages/Microsoft.Bcl.Simd), et le réseau de réseau apI tels que ceux trouvés dans l’espace de nom sont maintenant disponibles sous forme <xref:System.Net.Http> de paquets open-source sur [GitHub](https://github.com/). Pour accéder au code, voir [.NET sur GitHub](https://github.com/dotnet/runtime). Pour plus d’informations, notamment sur la manière de contribuer à ces packages, consultez [.NET Core et Open-Source](../get-started/net-core-and-open-source.md), la [page d’accueil .NET sur GitHub](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>Nouveautés de .NET Framework 4.5.2

- **Nouvelles API pour les applications ASP.NET.** Les nouvelles méthodes <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> et <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> vous permettent d'inspecter et de modifier les en-têtes de réponse et le code d'état au moment où la réponse est vidée dans l'application cliente. Envisagez d'utiliser ces méthodes au lieu des événements <xref:System.Web.HttpApplication.PreSendRequestHeaders> et <xref:System.Web.HttpApplication.PreSendRequestContent> ; elles sont plus efficaces et fiables.

  La méthode <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> vous permet de planifier des petits éléments de travail en arrière-plan. ASP.NET effectue le suivi de ces éléments et empêche IIS de mettre fin brutalement au processus de traitement tant que tous les éléments de travail en arrière-plan ne sont pas terminés. Cette méthode ne peut pas être appelée en dehors d'un domaine d'application managée ASP.NET.

  Les nouvelles propriétés <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> et <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> retournent des valeurs booléennes qui indiquent si les en-têtes de réponse ont été écrits. Vous pouvez utiliser ces propriétés pour vous assurer que les appels d'API comme <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (qui lèvent des exceptions si les en-têtes ont été écrits) vont réussir.

- **Redimensionnement dans les contrôles Windows Forms** Cette fonctionnalité a été étendue. Vous pouvez maintenant utiliser le paramètre PPP système pour redimensionner les composants des contrôles supplémentaires suivants (par exemple, la flèche déroulante vers le bas dans les zones de liste modifiable) :

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Il est nécessaire d'accepter cette fonctionnalité. Pour l'activer, affectez à l'élément `EnableWindowsFormsHighDpiAutoResizing` la valeur `true` dans le fichier de configuration de l'application (app.config) :

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Nouvelle fonctionnalité de flux de travail.** Un gestionnaire de ressources qui utilise la méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> (et qui implémente donc l'interface <xref:System.Transactions.IPromotableSinglePhaseNotification>) peut utiliser la nouvelle méthode <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> pour demander :

  - La promotion de la transaction en transaction MSDTC (Microsoft Distributed Transaction Coordinator)

  - le remplacement de <xref:System.Transactions.IPromotableSinglePhaseNotification> par <xref:System.Transactions.ISinglePhaseNotification>, qui correspond à une inscription durable qui prend en charge les validations en une seule phase.

  Ces demandes peuvent être faites au sein du même domaine d'application et ne nécessitent pas de code non managé supplémentaire pour interagir avec MSDTC pour effectuer la promotion. La nouvelle méthode peut uniquement être appelée quand il existe un appel en suspens de <xref:System.Transactions?displayProperty=nameWithType> à la méthode <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` qui est implémentée par l’inscription pouvant être promue.

- **Améliorations du profilage.** Les nouvelles API de profilage non managées suivantes proposent un profilage plus robuste :

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO, structure](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [COR_PRF_MODULE_FLAGS, énumération](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences, méthode](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2, méthode](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2, méthode](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference, méthode](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Les implémentations précédentes d'`ICorProfiler` prenaient en charge le chargement tardif des assemblys dépendants. Les nouvelles API de profilage ont besoin que les assemblys dépendants soient injectés par le profileur pour qu'ils puissent être chargés immédiatement, plutôt qu'une fois que l'application est entièrement initialisée. Cette modification ne concerne pas les utilisateurs des API `ICorProfiler` existantes.

- **Améliorations du débogage.** Les nouvelles API de débogage non managées suivantes améliorent l'intégration à un profileur. Vous pouvez à présent accéder aux métadonnées insérées par le profileur ainsi qu'aux variables locales et au code produit par les demandes ReJIT du compilateur pendant le débogage de dump.

  - [SetWriteableMetadataUpdateMode, méthode](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx, méthode](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx, méthode](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx, méthode](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode, méthode](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap, méthode](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Modifications du suivi d’événements.** .NET Framework 4.5.2 permet le traçage des activités de type Suivi d’événements pour Windows (ETW) hors processus pour une surface d’exposition plus importante. Ce dernier permet aux fournisseurs de gestion avancée de l'alimentation (APM) de fournir des outils légers qui suivent avec précision les coûts des demandes et activités individuelles qui traversent les threads.  Ces événements sont déclenchés uniquement quand les contrôleurs ETW les autorisent ; par conséquent, les modifications ne concernent pas le code ETW écrit auparavant ni le code qui s'exécute avec la fonctionnalité ETW désactivée.

- **Promotion d’une transaction et sa conversion en une inscription durable**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> est une nouvelle API ajoutée à .NET Framework 4.5.2 et 4.6 :

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  La méthode peut être utilisée par une inscription précédemment créée par <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> en réponse à la méthode <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType>. Elle demande à `System.Transactions` de promouvoir la transaction en une transaction MSDTC et de « convertir » l'inscription à promouvoir en une inscription durable. Après que la méthode s'est terminée avec succès, l'interface <xref:System.Transactions.IPromotableSinglePhaseNotification> n'est plus référencée par `System.Transactions` et toutes les futures notifications parviennent sur l'interface <xref:System.Transactions.ISinglePhaseNotification> fournie. L'inscription en question doit agir comme inscription durable, en prenant en charge la récupération et la journalisation des transactions. Consultez <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> pour plus d'informations. En outre, l'inscription doit prendre en charge <xref:System.Transactions.ISinglePhaseNotification>.  Cette méthode peut être appelée *seulement* lors du traitement d’un appel <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType>. Si tel n'est pas le cas, une exception <xref:System.Transactions.TransactionException> est levée.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>Nouveautés de .NET Framework 4.5.1

**Mises à jour d’avril 2014** :

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) inclut les mises à jour des modèles de la bibliothèque de classes portable pour prendre en charge les scénarios suivants :

  - Vous pouvez utiliser les API Windows Runtime dans les bibliothèques portables qui ciblent Windows 8.1, Windows Phone 8.1, et Windows Phone Silverlight 8.1.

  - Vous pouvez inclure du code XAML (type Windows.UI.XAML) dans les bibliothèques portables quand vous ciblez Windows 8.1 ou Windows Phone 8.1. Les modèles XAML suivants sont pris en charge : Page vierge, Dictionnaire de ressources, Contrôle basé sur un modèle et Contrôle utilisateur.

  - Vous pouvez créer un composant Windows Runtime portable (fichier .winmd) à utiliser dans les applications du Windows Store qui ciblent Windows 8.1 et Windows Phone 8.1.

  - Vous pouvez recibler une bibliothèque de classes du Windows Store ou du Windows Phone Store, par exemple une bibliothèque de classes portable.

  Pour plus d’informations sur ces modifications, consultez [Bibliothèque de classes portable](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Le jeu de contenus du .NET Framework inclut à présent la documentation relative à .NET Native, une technologie de précompilation qui permet de générer et déployer des applications Windows. .NET Native compile directement vos applications en code natif, plutôt qu'en langage intermédiaire, pour de meilleures performances. Pour plus d’informations, consultez [Compilation d’applications avec .NET Native](../net-native/index.md).

- Le site [.NET Framework Reference Source](https://referencesource.microsoft.com/) propose une nouvelle expérience de navigation et des fonctionnalités améliorées. Vous pouvez à présent parcourir le code source .NET Framework en ligne, [télécharger la référence](https://referencesource.microsoft.com/download.html) à des fins de consultation hors connexion et parcourir les sources (notamment les correctifs et mises à jour) pendant le débogage. Pour plus d’informations, consultez l’entrée de blog qui présente [le nouvel aspect de la source de référence .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Les nouvelles fonctionnalités et améliorations des classes de base de .NET Framework 4.5.1 incluent les suivantes :

- Redirection de liaison automatique des assemblys. Depuis Visual Studio 2013, lorsque vous compilez une application qui cible le .NET Framework 4.5.1, il est possible d'ajouter des redirections de liaison au fichier de configuration de l'application, si votre application ou ses composants référencent plusieurs versions du même assembly. Vous pouvez également activer cette fonctionnalité pour les projets qui ciblent des versions antérieures du .NET Framework. Pour plus d’informations, consultez [Guide pratique pour activer et désactiver la redirection de liaison automatique](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Capacité à collecter des informations de diagnostic pour aider les développeurs à améliorer les performances des applications serveur et cloud. Pour plus d'informations, consultez les méthodes <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> et <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> de la classe <xref:System.Diagnostics.Tracing.EventSource>.

- Capacité à compacter explicitement le tas d'objets volumineux (LOH) pendant un garbage collection. Pour plus d'informations, consultez la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>.

- Autres améliorations des performances, telles que la suspension d'application ASP.NET, les améliorations JIT multicœurs et le démarrage accéléré des applications après une mise à jour du .NET Framework. Pour plus d’informations, consultez l’article [Annonce de .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) et le billet de blog [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/).

Les améliorations apportées à Windows Forms incluent :

- Redimensionnement dans les contrôles Windows Forms. Vous pouvez utiliser le paramètre PPP système pour redimensionner les composants des contrôles (par exemple, les icônes qui apparaissent dans une grille des propriétés) en choisissant de l'utiliser pour votre application grâce à une entrée dans le fichier de configuration de l'application (app.config). Cette fonctionnalité est actuellement prise en charge dans les contrôles Windows Forms suivants :

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  -     Certains aspects de <xref:System.Windows.Forms.DataGridView> (consultez [Nouvelles fonctionnalités dans 4.5.2](#v452) pour connaître les autres contrôles pris en charge)

  Pour activer cette fonctionnalité, ajoutez un nouvel élément \<appSettings> au fichier de configuration (app.config) et affectez la valeur `true` à l'élément `EnableWindowsFormsHighDpiAutoResizing` :

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Les améliorations lors du débogage de vos applications .NET Framework dans Visual Studio 2013 incluent :

- Valeurs de retour dans le débogueur Visual Studio. Lorsque vous déboguez une application managée dans Visual Studio 2013, la Fenêtre Automatique affiche les types et les valeurs de retour pour les méthodes. Ces informations sont disponibles pour les applications de bureau, Windows Store et Windows Phone. Pour plus d’informations, consultez [Examiner les valeurs de retour des appels de méthode](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Modifier & Continuer pour applications 64 bits. Visual Studio 2013 prend en charge la fonctionnalité Modifier & Continuer pour les applications managées 64 bits pour le Bureau, Windows Store et Windows Phone. Les limitations existantes restent effectives pour les applications 32 bits et 64 bits (consultez la dernière section de l’article [Modifications de code prises en charge (C#)](/visualstudio/debugger/supported-code-changes-csharp)).

- Débogage asynchrone. Pour simplifier le débogage des applications asynchrones dans Visual Studio 2013, la pile d'appels masque le code d'infrastructure fourni par les compilateurs pour prendre en charge la programmation asynchrone. Elle chaîne également les trames parentes logiques afin que vous puissiez suivre plus clairement l'exécution logique du programme. Une fenêtre Tâches remplace la fenêtre Tâches parallèles et affiche les tâches relatives à un point d'arrêt particulier, ainsi que toutes les autres tâches qui sont actuellement actives ou planifiées dans l'application. Vous pouvez en savoir plus sur cette fonctionnalité en lisant la section sur le débogage asynchrone de l’[annonce relative à .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Meilleure prise en charge des exceptions pour les composants Windows Runtime. Dans Windows 8.1, une exception qui provient des applications Windows Store conserve les informations sur l'erreur qui a provoqué l'exception, même au-delà des limites du langage. Vous pouvez en savoir plus sur cette fonctionnalité en lisant la section sur le développement d’applications du Windows Store dans l’[annonce relative au .NET Framework 4.5.1](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Depuis Visual Studio 2013, vous pouvez utiliser [Mpgo.exe (Outil d'optimisation guidée par profil managé)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) pour optimiser les applications Windows 8.x Store, ainsi que les applications de bureau.

Pour les nouvelles fonctionnalités dans ASP.NET 4.5.1, consultez [Notes de mise à jour ASP.NET et Web Tools pour Visual Studio 2013](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>Nouveautés de .NET Framework 4.5

### <a name="base-classes"></a>Classes de base

- Capacité à réduire les redémarrages du système en détectant et en fermant les applications .NET Framework 4 pendant le déploiement. Consultez [Réduction des redémarrages système durant les installations de .NET Framework 4.5](../deployment/reducing-system-restarts.md).

- Prise en charge de tableaux supérieurs à 2 gigaoctets (Go) sur les plateformes 64 bits. Cette fonctionnalité peut être activée dans le fichier de configuration de l'application. Voir le [ \<gcAllowVeryLargeObjects> élément](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), qui énumère également d’autres restrictions sur la taille de l’objet et la taille du tableau.

- Meilleures performances via une opération garbage collection en arrière-plan pour les serveurs. Lorsque vous utilisez le garbage collection de serveur dans .NET Framework 4.5, le garbage collection en arrière-plan est automatiquement activé. Consultez la section Garbage collection de serveur en arrière-plan, dans la rubrique [Notions de base du garbage collection](../../standard/garbage-collection/fundamentals.md).

- Compilation juste-à-temps (JIT) en arrière-plan, disponible en option sur les processeurs multicœurs pour améliorer les performances de l'application. Consultez <xref:System.Runtime.ProfileOptimization>.

- Capacité de limiter combien de temps le moteur d’expression régulière tentera de résoudre une expression régulière avant qu’il ne s’évanouit. Voir <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> la propriété.

- Capacité à définir la culture par défaut d'un domaine d'application. Consultez la classe <xref:System.Globalization.CultureInfo>.

- Prise en charge de la console pour l'encodage Unicode (UTF-16). Consultez la classe <xref:System.Console>.

- Prise en charge du versioning des données de classement et de comparaison des chaînes culturelles. Consultez la classe <xref:System.Globalization.SortVersion>.

- Meilleures performances lors de l'extraction des ressources. Consultez [Empaquetage et déploiement de ressources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Améliorations de la compression Zip pour réduire la taille d'un fichier compressé. Voir l'espace de noms <xref:System.IO.Compression?displayProperty=nameWithType>.

- Possibilité de personnaliser un contexte de réflexion pour remplacer le comportement de réflexion par défaut par l'intermédiaire de la classe <xref:System.Reflection.Context.CustomReflectionContext>.

- Prise en charge de la version 2008 de la norme <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> Internationalized Domain Names in Applications (IDNA) lorsque la classe est utilisée sur Windows 8.

- Délégation de comparaison de chaînes au système d'exploitation, qui implémente Unicode 6.0, lorsque .NET Framework est utilisé dans Windows 8. Lorsqu'il s'exécute sur d'autres plateformes, .NET Framework inclut ses propres données de comparaison de chaînes, qui implémentent Unicode 5.x. Voir la classe <xref:System.String> et la section Notes de la classe <xref:System.Globalization.SortVersion>.

- Possibilité de calculer les codes de hachage des chaînes par domaine d'application. Voir [ \<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Prise en charge de la réflexion de type fractionnée entre les classes <xref:System.Type> et <xref:System.Reflection.TypeInfo>. Consultez [Réflexion dans le .NET Framework pour les applications du Windows Store](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Dans le .NET Framework 4.5, le package Managed Extensibility Framework (MEF) fournit les nouvelles fonctionnalités suivantes :

- Prise en charge des types génériques.

- Modèle de programmation basé sur les conventions qui permet de créer des parties basées sur les conventions d'appellation, plutôt que sur les attributs.

- Portées multiples.

- Sous-ensemble MEF que vous pouvez utiliser lorsque vous créez des applications Windows 8.x Store. Ce sous-ensemble est disponible sous la forme d’un [package téléchargeable](https://www.nuget.org/packages/Microsoft.Composition) à partir de la galerie NuGet. Pour installer ce package, ouvrez votre projet dans Visual Studio, dans le menu **Projet** choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Composition`.

Pour plus d’informations, consultez [Vue d’ensemble de Managed Extensibility Framework](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Opérations asynchrones sur les fichiers

Dans le .NET Framework 4.5, de nouvelles fonctionnalités asynchrones ont été ajoutées aux langages C# et Visual Basic. Ces fonctionnalités ajoutent un modèle basé sur les tâches pour exécuter des opérations asynchrones. Pour utiliser ce nouveau modèle, utilisez les méthodes asynchrones dans les classes d'E/S. Consultez [E/S de fichier asynchrone](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Outils

Dans le .NET Framework 4.5, l'outil Resource File Generator (Resgen.exe) vous permet de créer un fichier .resw à utiliser dans les applications Windows 8.x Store à partir d'un fichier .resources incorporé dans un assembly .NET Framework. Pour plus d’informations, consultez [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).

L'outil d'optimisation guidée par profil managé (Mpgo.exe) vous permet d'améliorer le temps de démarrage de l'application, l'utilisation de la mémoire (taille du jeu de travail) et le débit en optimisant les assemblys d'image natifs. L'outil en ligne de commande génère des données de profil pour les assemblys natifs d'application graphique. Consultez [Mpgo.exe (Outil d’optimisation guidée par profil managé)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Depuis Visual Studio 2013, vous pouvez utiliser Mpgo.exe pour optimiser les applications Windows 8.x Store, ainsi que les applications de bureau.

<a name="parallel" />

### <a name="parallel-computing"></a>Calcul parallèle

Le .NET Framework 4.5 fournit plusieurs nouvelles fonctionnalités et améliorations pour le calcul parallèle. Il s'agit notamment de performances améliorées, d'un contrôle accru, d'une prise en charge améliorée pour la programmation asynchrone, d'une nouvelle bibliothèque de flux de données et d'une prise en charge améliorée pour le débogage parallèle et l'analyse des performances. Consultez l’entrée relative aux [nouveautés en matière de parallélisme dans .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) dans le blog consacré à la programmation parallèle avec .NET.

<a name="web" />

### <a name="web"></a>Web

ASP.NET 4.5 et 4.5.1 ajoutent la liaison de modèle pour Web Forms, la prise en charge de WebSocket, les gestionnaires asynchrones, les améliorations de performances et de nombreuses autres fonctionnalités. Pour plus d’informations, consultez les ressources suivantes :

- [ASP.NET 4.5 et Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [ASP.NET et Web Tools pour Visual Studio 2013 - Notes de publication](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a>Réseaux <a name="networking" />

Le .NET Framework 4.5 fournit une nouvelle interface de programmation pour les applications HTTP. Pour plus d'informations, consultez les nouveaux espaces de noms <xref:System.Net.Http?displayProperty=nameWithType> et <xref:System.Net.Http.Headers?displayProperty=nameWithType>.

La prise en charge d'une nouvelle interface de programmation permettant d'accepter et d'interagir avec une connexion de WebSocket à l'aide de la classe <xref:System.Net.HttpListener> existante et des classes associées est également incluse. Pour plus d'informations, consultez le nouvel espace de noms <xref:System.Net.WebSockets> et la classe <xref:System.Net.HttpListener>.

En outre, le .NET Framework 4.5 inclut les améliorations de mise en réseau suivantes :

- Prise en charge URI conforme aux documents RFC. Pour plus d'informations, consultez <xref:System.Uri> et les classes associées.

- Prise en charge des analyses du nom de domaine international (IDN, Internationalized Domain Name). Pour plus d'informations, consultez <xref:System.Uri> et les classes associées.

- Prise en charge de l'internationalisation des adresses de messagerie. Pour plus d'informations, consultez l'espace de noms <xref:System.Net.Mail>.

- Prise en charge d'IPv6 améliorée. Pour plus d'informations, consultez l'espace de noms <xref:System.Net.NetworkInformation>.

- Prise en charge du socket en mode double. Pour plus d'informations, consultez la classe <xref:System.Net.Sockets.Socket> et <xref:System.Net.Sockets.TcpListener>.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Dans le .NET Framework 4.5, Windows Presentation Foundation (WPF) présente des modifications et des améliorations dans les domaines suivants :

- Le nouveau contrôle <xref:System.Windows.Controls.Ribbon.Ribbon>, qui vous permet d'implémenter une interface utilisateur de type ruban hébergeant une barre d'outils Accès rapide, un menu d'application et des onglets.

- La nouvelle interface <xref:System.ComponentModel.INotifyDataErrorInfo>, qui prend en charge la validation synchrone et asynchrone des données.

- Nouvelles fonctionnalités des classes <xref:System.Windows.Controls.VirtualizingPanel> et <xref:System.Windows.Threading.Dispatcher>.

- Performances améliorées lors de l'affichage de grands ensembles de données groupées et lors de l'accès aux collections sur les threads autres que ceux d'interface utilisateur.

- Liaison de données aux propriétés statiques, liaison de données aux types personnalisés qui implémentent l'interface <xref:System.Reflection.ICustomTypeProvider> et extraction des informations de liaison de données à partir d'une expression de liaison.

- Repositionnement des données au fur et à mesure du changement des valeurs (mise en forme active).

- Possibilité de vérifier si le contexte de données d'un conteneur d'éléments est déconnecté.

- Possibilité de définir la durée qui doit s'écouler entre les modifications de propriété et les mises à jour de la source de données.

- Prise en charge améliorée pour implémenter des modèles d'événement faible. De plus, les événements peuvent maintenant accepter des extensions de balisage.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Dans le .NET Framework 4.5, les fonctionnalités suivantes ont été ajoutées pour faciliter l'écriture et l'entretien des applications Windows Communication Foundation (WCF) :

- Simplification des fichiers de configuration générés.

- Prise en charge du développement Contrat en premier.

- Possibilité de configurer plus facilement le mode de compatibilité ASP.NET.

- Modifications des valeurs de propriété de transport par défaut pour réduire la probabilité d'avoir à les définir.

- Mises à jour de la classe <xref:System.Xml.XmlDictionaryReaderQuotas> afin de réduire la probabilité d'avoir à configurer manuellement les quotas pour les lecteurs de dictionnaire XML.

- Validation des fichiers de configuration WCF par Visual Studio dans le cadre du processus de génération, afin que vous puissiez détecter les erreurs de configuration avant d'exécuter votre application.

- Nouvelle prise en charge de la diffusion en continu asynchrone.

- Nouveau mappage de protocole HTTPS pour simplifier l'exposition d'un point de terminaison via HTTPS à l'aide des services Internet (IIS).

- Possibilité de générer des métadonnées dans un document WSDL unique en ajoutant `?singleWSDL` à l'URL de service.

- Prise en charge Websockets pour activer une véritable communication bidirectionnelle sur les ports 80 et 443 avec des caractéristiques de performances semblables à celles du transport TCP.

- Prise en charge de la configuration des services dans le code.

- Info-bulles de l'éditeur XML.

- Prise en charge de la mise en cache de <xref:System.ServiceModel.ChannelFactory>.

- Prise en charge de la compression d'encodage binaire.

- Prise en charge d'un transport UDP qui permet aux développeurs d'écrire des services qui utilisent une messagerie de type « Fire and Forget » (déclenché et oublié). Un client envoie un message à un service et n'attend aucune réponse de ce dernier.

- Possibilité de prendre en charge plusieurs modes d'authentification sur un point de terminaison WCF unique lors de l'utilisation du transport HTTP et de la sécurité du transport.

- Prise en charge des services WCF qui utilisent des noms IDN.

Pour plus d’informations, consultez [Nouveautés dans Windows Communication Foundation](../wcf/whats-new.md).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

Dans le .NET Framework 4.5, plusieurs nouvelles fonctionnalités ont été ajoutées à Windows Workflow Foundation (WF), notamment :

- Flux de travail de la machine à états, qui ont été introduits pour la première fois dans le cadre de .NET Framework 4.0.1 ([Mise à jour 1 de la plateforme .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)). Cette mise à jour comprenait plusieurs classes et activités nouvelles qui permettaient aux développeurs de créer des flux de travail de machine à états. Ces classes et activités ont été mises à jour pour que le .NET Framework 4.5 inclue les fonctionnalités suivantes :

  - Possibilité de définir des points d'arrêt sur les états.

  - Possibilité de copier et coller des transitions dans le concepteur de workflow.

  - Prise en charge du concepteur pour la création de transitions de déclencheur partagées.

  - Activités de création de flux de travail de machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>.

- Fonctionnalités améliorées du Concepteur de flux de travail, dont notamment :

  - Fonctions de recherche de flux de travail améliorées dans Visual Studio, notamment **Recherche rapide** et **Rechercher dans les fichiers**.

  - Possibilité de créer automatiquement une activité de séquence lorsqu'une deuxième activité enfant est ajoutée à une activité de conteneur, et d'inclure les deux activités dans l'activité de séquence.

  - Prise en charge des panoramiques, ce qui permet à la partie visible d'un flux de travail d'être modifiée sans utiliser les barres de défilement.

  - Nouvelle vue **Structure du document** qui affiche les composants d’un flux de travail en mode Plan sous forme d’arborescence et vous permet de sélectionner un composant dans la vue **Structure du document**.

  - Possibilité d'ajouter des annotations aux activités.

  - Possibilité de définir et d'utiliser des délégués d'activité à l'aide du Concepteur de flux de travail.

  - Connexion automatique et insertion automatique des activités et des transitions dans les flux de travail de machine à états et d'organigramme.

- Stockage des informations d'état d'affichage pour un flux de travail dans un élément unique du fichier XAML, afin que vous puissiez facilement localiser et modifier les informations sur l'état d'affichage.

- Activité de conteneur NoPersistScope pour empêcher les activités enfants de devenir persistantes.

- Prise en charge des expressions C# :

  - Les projets de flux de travail qui utilisent Visual Basic utiliseront les expressions Visual Basic et les projets de flux de travail C# utiliseront les expressions C#.

  - Les projets de flux de travail C# qui ont été créés dans Visual Studio 2010 et qui possèdent des expressions Visual Basic sont compatibles avec les projets de flux de travail C# qui utilisent des expressions C#.

- Améliorations du contrôle de version :

  - Nouvelle classe <xref:System.Activities.WorkflowIdentity>, qui fournit un mappage entre une instance de flux de travail rendue persistante et sa définition de flux de travail.

  - Exécution côte à côte de plusieurs versions de flux de travail dans le même hôte, y compris <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

  - Dans une mise à jour dynamique, capacité à modifier la définition d'une instance de flux de travail rendue persistante.

- Développement de services de workflow « Contrat en premier », ce qui permet de générer automatiquement les activités correspondants à un contrat de service existant.

Pour plus d’informations, consultez [Nouveautés de Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a>.NET pour les applications Windows 8.x Store

Les applications Windows 8.x Store sont conçues pour des facteurs de forme spécifiques et tirent parti de la puissance du système d'exploitation Windows. Un sous-ensemble du .NET Framework 4.5 ou 4.5.1 est disponible pour générer des applications Windows 8.x Store pour Windows à l'aide de C# ou de Visual Basic. Ce sous-ensemble est appelé .NET pour Windows 8.x Store applications et est discuté dans un [aperçu](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

### <a name="portable-class-libraries"></a>Bibliothèques de classes portables<a name="portable" />

Le projet Bibliothèque de classes portable dans Visual Studio 2012 (et les versions ultérieures) vous permet d'écrire et de générer des assemblys managés qui fonctionnent sur plusieurs plateformes .NET Framework. À l’aide d’un projet de bibliothèque de classe portable, vous choisissez les plates-formes (telles que Windows Phone et .NET pour windows 8.x Store applications) à cibler. Les types et les membres disponibles dans votre projet sont automatiquement restreints aux types et aux membres communs entre ces plateformes. Pour plus d’informations, consultez [Bibliothèque de classes portable](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Voir aussi

- [Versions finales hors plage de .NET Framework](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Nouveautés du .NET Framework dans le domaine de l’accessibilité](whats-new-in-accessibility.md)
- [Quoi de neuf dans Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Nouveautés dans Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Nouveautés de C++ dans Visual Studio](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
