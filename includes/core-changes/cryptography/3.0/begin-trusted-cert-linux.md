---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721423"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="d607b-101">La syntaxe « BEGIN TRUSTed CERTIFICATe » n’est plus prise en charge pour les certificats racines sur Linux</span><span class="sxs-lookup"><span data-stu-id="d607b-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="d607b-102">Les certificats racine sur Linux et d’autres systèmes de type UNIX (mais pas macOS) peuvent être présentés sous deux formes : l' `BEGIN CERTIFICATE` en-tête PEM standard et l' `BEGIN TRUSTED CERTIFICATE` en-tête PEM spécifique à OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="d607b-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="d607b-103">La dernière syntaxe permet une configuration supplémentaire qui a provoqué des problèmes de compatibilité avec la classe de .NET Core <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="d607b-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="d607b-104">`BEGIN TRUSTED CERTIFICATE`le contenu du certificat racine n’est plus chargé par le moteur de chaîne à partir de .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d607b-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d607b-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d607b-105">Change description</span></span>

<span data-ttu-id="d607b-106">Auparavant, les `BEGIN CERTIFICATE` `BEGIN TRUSTED CERTIFICATE` syntaxes et étaient utilisées pour remplir la liste d’approbation racine.</span><span class="sxs-lookup"><span data-stu-id="d607b-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="d607b-107">Si la `BEGIN TRUSTED CERTIFICATE` syntaxe a été utilisée et que des options supplémentaires ont été spécifiées dans le fichier, <xref:System.Security.Cryptography.X509Certificates.X509Chain> il est possible qu’elle ait signalé que l’approbation de chaîne a été explicitement interdite ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="d607b-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="d607b-108">Toutefois, si le certificat a également été spécifié avec la `BEGIN CERTIFICATE` syntaxe dans un fichier précédemment chargé, l’approbation de chaîne était autorisée.</span><span class="sxs-lookup"><span data-stu-id="d607b-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="d607b-109">À compter de .NET Core 3,0, le `BEGIN TRUSTED CERTIFICATE` contenu n’est plus lu.</span><span class="sxs-lookup"><span data-stu-id="d607b-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="d607b-110">Si le certificat n’est pas également spécifié via une `BEGIN CERTIFICATE` syntaxe standard, le <xref:System.Security.Cryptography.X509Certificates.X509Chain> signale que la racine n’est pas approuvée ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="d607b-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d607b-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d607b-111">Version introduced</span></span>

<span data-ttu-id="d607b-112">3.0</span><span class="sxs-lookup"><span data-stu-id="d607b-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d607b-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d607b-113">Recommended action</span></span>

<span data-ttu-id="d607b-114">La plupart des applications ne sont pas affectées par cette modification, mais les applications qui ne peuvent pas voir les sources de certificat racine en raison de problèmes d’autorisations peuvent rencontrer des erreurs inattendues `UntrustedRoot` après la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="d607b-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="d607b-115">De nombreuses distributions Linux (ou distributions) écrivent des certificats racine dans deux emplacements : un répertoire à un certificat par fichier et une concaténation de fichier unique.</span><span class="sxs-lookup"><span data-stu-id="d607b-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="d607b-116">Sur certains distributions, le répertoire à un certificat par fichier utilise la `BEGIN TRUSTED CERTIFICATE` syntaxe, tandis que la concaténation de fichier utilise la `BEGIN CERTIFICATE` syntaxe standard.</span><span class="sxs-lookup"><span data-stu-id="d607b-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="d607b-117">Assurez-vous que tous les certificats racines personnalisés sont ajoutés comme `BEGIN CERTIFICATE` dans au moins l’un de ces emplacements et que les deux emplacements peuvent être lus par votre application.</span><span class="sxs-lookup"><span data-stu-id="d607b-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="d607b-118">Le répertoire par défaut est */etc/SSL/certs/* et le fichier concaténé standard est */etc/ssl/cert.pem*.</span><span class="sxs-lookup"><span data-stu-id="d607b-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="d607b-119">Utilisez la commande `openssl version -d` pour déterminer la racine spécifique à la plateforme, qui peut différer de */etc/SSL/*.</span><span class="sxs-lookup"><span data-stu-id="d607b-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="d607b-120">Par exemple, sur Ubuntu 18,04, le répertoire est */usr/lib/SSL/certs/* et le fichier est */usr/lib/SSL/CERT.pem*.</span><span class="sxs-lookup"><span data-stu-id="d607b-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="d607b-121">Toutefois, */usr/lib/SSL/certs/* est un lien symbolique vers */etc/SSL/certs/* et */usr/lib/SSL/CERT.pem* n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d607b-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a><span data-ttu-id="d607b-122">Category</span><span class="sxs-lookup"><span data-stu-id="d607b-122">Category</span></span>

<span data-ttu-id="d607b-123">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="d607b-123">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d607b-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="d607b-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
