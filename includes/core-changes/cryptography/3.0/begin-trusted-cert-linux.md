---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135596"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>La syntaxe « BEGIN TRUSTed CERTIFICATe » n’est plus prise en charge pour les certificats racines sur Linux

Les certificats racine sur Linux et d’autres systèmes de type UNIX (mais pas macOS) peuvent être présentés sous deux formes : `BEGIN CERTIFICATE` l’en-tête PEM standard et l' `BEGIN TRUSTED CERTIFICATE` en-tête PEM spécifique à OpenSSL. La dernière syntaxe permet une configuration supplémentaire qui a provoqué des problèmes de compatibilité avec la <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> classe de .net core. `BEGIN TRUSTED CERTIFICATE`le contenu du certificat racine n’est plus chargé par le moteur de chaîne à partir de .NET Core 3,0.

#### <a name="change-description"></a>Description de la modification

Auparavant, les `BEGIN CERTIFICATE` syntaxes `BEGIN TRUSTED CERTIFICATE` et étaient utilisées pour remplir la liste d’approbation racine. Si la `BEGIN TRUSTED CERTIFICATE` syntaxe a été utilisée et que des options supplémentaires ont été spécifiées dans le fichier, <xref:System.Security.Cryptography.X509Certificates.X509Chain> il est possible qu’elle ait signalé que<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>l’approbation de chaîne a été explicitement interdite (). Toutefois, si le certificat a également été spécifié avec `BEGIN CERTIFICATE` la syntaxe dans un fichier précédemment chargé, l’approbation de chaîne était autorisée.

À compter de .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` , le contenu n’est plus lu. Si le certificat n’est pas également spécifié via une `BEGIN CERTIFICATE` syntaxe standard, <xref:System.Security.Cryptography.X509Certificates.X509Chain> le signale que la racine n’est<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>pas approuvée ().

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La plupart des applications ne sont pas affectées par cette modification, mais les applications qui ne peuvent pas voir les sources de certificat `UntrustedRoot` racine en raison de problèmes d’autorisations peuvent rencontrer des erreurs inattendues après la mise à niveau.

De nombreuses distributions Linux (ou distributions) écrivent des certificats racine dans deux emplacements : un répertoire à un certificat par fichier et une concaténation de fichier unique. Sur certains distributions, le répertoire à un certificat par fichier utilise la `BEGIN TRUSTED CERTIFICATE` syntaxe, tandis que la concaténation de fichier utilise `BEGIN CERTIFICATE` la syntaxe standard. Assurez-vous que tous les certificats racines `BEGIN CERTIFICATE` personnalisés sont ajoutés comme dans au moins l’un de ces emplacements et que les deux emplacements peuvent être lus par votre application.

Le répertoire par défaut est */etc/SSL/certs/* et le fichier concaténé standard est */etc/ssl/cert.pem*. Utilisez la commande `openssl version -d` pour déterminer la racine spécifique à la plateforme, qui peut différer de */etc/SSL/*. Par exemple, sur Ubuntu 18,04, le répertoire est */usr/lib/SSL/certs/* et le fichier est */usr/lib/SSL/CERT.pem*. Toutefois, */usr/lib/SSL/certs/* est un lien symbolique vers */etc/SSL/certs/* et */usr/lib/SSL/CERT.pem* n’existe pas.

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

### <a name="category"></a>Category

Chiffrement

### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
