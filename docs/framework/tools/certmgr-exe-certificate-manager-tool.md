---
title: Certmgr.exe (outil de gestionnaire de certificats)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad7ce5dd3739b1edcf8a8a03a2f57376ceba138
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948589"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (outil de gestionnaire de certificats)
L'outil Certificate Manager (Certmgr.exe) gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour démarrer l’outil, utilisez des [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
> L'outil Certificate Manager (Certmgr.exe) est un utilitaire en ligne de commande, alors que Certificats (Certmgr.msc) est un composant logiciel enfichable MMC (Microsoft Management Console). Comme Certmgr.msc se trouve généralement dans le répertoire système de Windows, quand vous entrez `certmgr` sur la ligne de commande, vous pouvez charger le composant logiciel enfichable MMC Certificats même si vous avez ouvert l'invite de commandes développeur pour Visual Studio. Cela se produit parce que le chemin d’accès au composant logiciel enfichable précède le chemin d’accès à l’outil Certificate Manager dans la variable d’environnement PATH. Si vous rencontrez ce problème, vous pouvez exécuter des commandes Certmgr.exe en spécifiant le chemin d'accès au fichier exécutable.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Pour une vue d'ensemble des certificats X.509, consultez [Utilisation des certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Argument|Description|  
|--------------|-----------------|  
|*sourceStorename*|Le magasin de certificats qui contient les certificats existants, les CTL ou CRL à ajouter, supprimer, enregistrer ou afficher. Il peut s'agir d'un fichier de magasin ou d'un magasin système.|  
|*destinationStorename*|Magasin ou fichier du certificat de sortie.|  
  
|Option|Description|  
|------------|-----------------|  
|**/add**|Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.|  
|**/all**|Ajoute toutes les entrées si utilisée avec **/add**. Supprime toutes les entrées si utilisée avec **/del**. Affiche toutes les entrées si utilisée sans les options **/add**, ni **/del**. L'option **/all** ne peut pas être utilisée avec **/put**.|  
|**/c**|Ajoute des certificats si utilisée avec **/add**. Supprime des certificats si utilisée avec **/del**. Enregistre des certificats si utilisée avec **/put**. Affiche des certificats si utilisée sans les options **/add**, **/del** ou **/put**.|  
|**/CRL**|Ajoute des listes de révocation de certificats si utilisée avec **/add**. Supprime des listes de révocation de certificats si utilisée avec **/del**. Enregistre des listes de révocation de certificats si utilisée avec **/put**. Affiche les listes de révocation des certificats si utilisée sans les options **/add**, **/del** ou **/put**.|  
|**/CTL**|Ajoute des listes de certificats de confiance si utilisée avec **/add**. Supprime des listes de certificats de confiance si utilisée avec **/del**. Enregistre des listes de certificats de confiance si utilisée avec **/put**. Affiche des listes de certificats de confiance si utilisée sans l'option **/add**, **/del** ou **/put**.|  
|**/del**|Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.|  
|**/e** *type d’encodage*|Spécifie le type d'encodage des certificats. La valeur par défaut est `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Spécifie l'indicateur d'ouverture du magasin. Il s'agit du paramètre *dwFlags* passé à **CertOpenStore**. Sa valeur par défaut est CERT_SYSTEM_STORE_CURRENT_USER. Cette option n'est prise en compte que si l'option **/y** est utilisée.|  
|**/h**[**elp**]|Affiche la syntaxe et les options de commande de l'outil.|  
|**/n** *nam*|Spécifie le nom commun du certificat à ajouter, à supprimer ou à enregistrer. Cette option ne peut être utilisée qu'avec des certificats ; elle n'est pas compatible avec les listes de certificats de confiance, ni avec les listes de révocation de certificats.|  
|**/put**|Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats. Le fichier est enregistré au format X.509. Vous pouvez utiliser l'option **/7** avec l'option **/put** pour enregistrer le fichier au format PKCS #7. L'option **/put** doit être suivie par **/c**, **/CTL** ou **/CRL**. L'option **/all** ne peut pas être utilisée avec **/put**.|  
|**/r** *emplacement*|Identifie l'emplacement du magasin système dans le Registre. Cette option n'est prise en compte que si l'option **/s** est spécifiée. La valeur de *location* doit être l'une des suivantes :<br /><br /> -   `currentUser` indique que le magasin de certificats se trouve sous la clé HKEY_CURRENT_USER. Il s'agit de la valeur par défaut.<br />-   `localMachine` indique que le magasin de certificats se trouve sous la clé HKEY_LOCAL_MACHINE.|  
|**/s**|Indique que le magasin de certificats est un magasin système. Si vous ne spécifiez pas cette option, le magasin est considéré comme **StoreFile**.|  
|**/sha1** *hachage sha1*|Spécifie le hachage SHA1 du certificat, de la liste de certificats de confiance ou de la liste de révocation de certificats à ajouter, à supprimer ou à enregistrer.|  
|**/v**|Spécifie le mode Commentaires ; affiche des informations détaillées sur les certificats, les listes de certificats de confiance et les listes de révocation de certificats. Vous ne pouvez pas utiliser cette option avec **/add**, **/del** ou **/put**.|  
|**/y** *fournisseur*|Spécifie le nom du fournisseur de magasin.|  
|**/7**|Enregistre le magasin de destination comme un objet PKCS #7.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Remarques  
 Certmgr.exe exécute les fonctions de base suivantes :  
  
- Affiche les certificats, listes de certificats de confiance et listes de révocation de certificats dans la console.  
  
- Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.  
  
- Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.  
  
- Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats.  
  
 Certmgr.exe fonctionne avec deux types de magasins de certificats : **StoreFile** et le magasin système. Il n'est pas nécessaire de spécifier le type de magasin de certificats ; Certmgr.exe est capable de l'identifier et d'effectuer les opérations appropriées.  
  
 L'exécution de Certmgr.exe sans aucune option lance le composant logiciel enfichable certmgr.msc, qui dispose d'une interface utilisateur graphique (GUI) qui facilite les tâches de gestion des certificats qui sont également disponibles à partir de la ligne de commande. Cette interface utilisateur graphique fournit un Assistant d'importation qui copie les certificats, les listes de certificats de confiance et les listes de révocation de certificats depuis votre disque vers un magasin de certificats.  
  
 Vous pouvez rechercher les noms de magasins de certificats X509 pour les paramètres `sourceStorename` et `destinationStorename` en compilant et en exécutant le code suivant.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Exemples  
 La commande suivante affiche un magasin système par défaut appelé `my` avec une sortie des commentaires.  
  
```  
certmgr /v /s my  
```  
  
 La commande suivante ajoute tous les certificats contenus dans un fichier nommé `myFile.ext` dans un nouveau fichier appelé `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 La commande suivante ajoute le certificat dans un fichier nommé `testcert.cer` au magasin système `my`.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 La commande suivante ajoute le certificat dans un fichier nommé `TrustedCert.cer` dans le magasin de certificats racines.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 La commande suivante enregistre un certificat avec le nom commun `myCert` dans le magasin système `my` vers un fichier nommé `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 La commande suivante supprime toutes les listes de certificats de confiance du magasin système `my` et enregistre le magasin qui en résulte dans un fichier nommé `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 La commande suivante enregistre un certificat dans le magasin système `my` du fichier `newFile`. Vous devez saisir le numéro du certificat de `my` à placer dans `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Voir aussi

- [Outils](../../../docs/framework/tools/index.md)
- [Makecert.exe (outil de création du certificat)](/windows/desktop/SecCrypto/makecert)
- [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
