---
title: Sn.exe (outil Strong Name Tool)
description: Prise en main de Sn.exe, l’outil Strong Name Tool. Signez les assemblys avec des noms forts. Gérer les clés et générer et vérifier les signatures.
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
ms.openlocfilehash: 8f10dab9b395640e46cb9bf3ca468b8f6bb2bc1b
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517189"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (outil Strong Name Tool)
L’outil Strong Name (Sn.exe) permet de signer des assemblys avec des [noms forts](../../standard/assembly/strong-named.md). Sn.exe fournit des options de gestion des clés, de génération des signatures et de vérification des signatures.  
  
> [!WARNING]
> Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

 Pour plus d’informations sur l’utilisation de noms forts et sur les assemblys portant des noms forts, consultez [Assemblys avec nom fort](../../standard/assembly/strong-named.md) et [Guide pratique pour signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour démarrer l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  

> [!NOTE]
> Sur les ordinateurs 64 bits, exécutez la version 32 bits de Sn.exe à l’aide de l’invite de commandes développeur pour Visual Studio et la version 64 bits à l’aide de l’invite de commandes Visual Studio x64 Win64.
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Option|Description|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Génère des données <xref:System.Reflection.AssemblySignatureKeyAttribute> pour migrer la clé d'identité vers la clé de signature d'un fichier.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Génère des données <xref:System.Reflection.AssemblySignatureKeyAttribute> pour migrer la clé d'identité à la clé de signature d'un conteneur de clé.|  
|`-c [csp]`|Définit le fournisseur de services de chiffrement par défaut à utiliser pour la signature avec un nom fort. Ce paramètre s'applique à l'ensemble de l'ordinateur. Si vous ne spécifiez pas de nom de fournisseur de services de chiffrement, Sn.exe supprime le paramètre en cours.|  
|`-d container`|Supprime le conteneur de clé spécifié du fournisseur de services de chiffrement de noms forts.|  
|`-D assembly1 assembly2`|Vérifie que deux assemblys ne se distinguent que par leur signature. Cette vérification intervient souvent après la nouvelle signature d'un assembly avec une paire de clés différente.|  
|`-e assembly outfile`|Extrait la clé publique de l’*assembly* et la stocke dans le *outfile*.|  
|`-h`|Affiche la syntaxe et les options de commande de l'outil.|  
|`-i infile container`|Installe la paire de clés d’*infile* dans le conteneur de clé spécifié. Le conteneur de clé réside dans le fournisseur de services de chiffrement de noms forts.|  
|`-k [keysize] outfile`|Génère une nouvelle clé <xref:System.Security.Cryptography.RSACryptoServiceProvider> de la taille spécifiée et l’écrit dans le fichier spécifié.  Une clé publique et une clé privée sont écrites dans le fichier.<br /><br /> Si vous ne spécifiez pas de taille de clé, une clé de 1 024 bits est générée par défaut si le fournisseur de services de chiffrement avancé Microsoft est installé ; sinon, une clé de 512 bits est générée.<br /><br /> Le paramètre *keysize* prend en charge des longueurs de clé allant de 384 bits à 16 384 bits dans des incréments de 8 bits si le fournisseur de services de chiffrement avancé Microsoft est installé.  Il prend en charge des longueurs de clé allant de 384 bits à 512 bits par incréments de 8 bits si le fournisseur de services de chiffrement de base Microsoft est installé.|  
|`-m [y|n]`|Spécifie si les conteneurs de clés sont propres à l'ordinateur ou à l'utilisateur. Si vous spécifiez *y*, les conteneurs de clés sont propres à l’ordinateur. Si vous spécifiez *n*, les conteneurs de clés sont propres à l’utilisateur.<br /><br /> Si ni y, ni n ne sont spécifiés, cette option affiche le paramètre actuel.|  
|`-o infile [outfile]`|Extrait la clé publique d’*infile* et la stocke dans un fichier .csv. Chaque octet de la clé publique est séparé par une virgule. Ce format s'avère utile pour les références de codage en dur aux clés sous forme de tableaux initialisés dans le code source. Si *outfile* n’est pas spécifié, cette option place la sortie dans le Presse-papiers. **Remarque :** Cette option ne vérifie pas si l’entrée est une clé publique uniquement. Si `infile` contient une paire de clés dont une est privée, la clé privée est également extraite.|  
|`-p infile outfile [hashalg]`|Extrait la clé publique de la paire de clés dans *infile* et la stocke dans *outfile*, éventuellement à l’aide de l’algorithme RSA spécifié par *hashalg*. Cette clé publique permet de différer la signature d’un assembly à l’aide des options **/delaysign+** et **/keyfile** d’[Assembly Linker (Al.exe)](al-exe-assembly-linker.md). En cas signature différée d'un assembly, seule la clé publique est définie au moment de la compilation et un espace est réservé dans le fichier pour la signature qui sera ajoutée par la suite, lorsque la clé privée sera connue.|  
|`-pc container outfile [hashalg]`|Extrait la clé publique de la paire de clés figurant dans *container* et la stocke dans *outfile*. Si vous utilisez l’option *hashalg*, l’algorithme RSA est utilisé pour récupérer la clé publique.|  
|`-Pb [y|n]`|Spécifie si la stratégie permettant d'ignorer les noms forts est appliquée. Si vous spécifiez *y*, les noms forts pour les assemblys à confiance totale ne sont pas validés en cas de chargement dans un <xref:System.AppDomain> à confiance totale. Si vous spécifiez *n*, l’exactitude des noms forts est validée, mais pas pour un nom fort spécifique. Le <xref:System.Security.Permissions.StrongNameIdentityPermission> n'a aucun effet sur les assemblys à confiance totale. Vous devez procéder à votre propre contrôle pour une correspondance de nom fort.<br /><br /> Si ni `y`, ni `n` ne sont spécifiés, cette option affiche le paramètre actuel. Par défaut, il s’agit de `y`. **Remarque :** Sur les ordinateurs 64 bits, vous devez définir ce paramètre à la fois sur l’instance 32 bits et sur l’instance 64 bits de Sn.exe.|  
|`-q[uiet]`|Spécifie le mode silencieux ; supprime l'affichage des messages d'opération réussie.|  
|`-R[a] assembly infile`|Resigne un assembly ayant préalablement fait l’objet d’une signature ou dont la signature a été différée avec la paire de clés figurant dans *infile*.<br /><br /> Si **-Ra** est utilisé, les hachages sont recalculés pour tous les fichiers de l’assembly.|  
|`-Rc[a] assembly container`|Resigne un assembly ayant préalablement fait l’objet d’une signature ou dont la signature a été différée avec la paire de clés figurant dans *container*.<br /><br /> Si **-Rca** est utilisé, les hachages sont recalculés pour tous les fichiers de l’assembly.|  
|`-Rh assembly`|Recalcule des hachages pour tous les fichiers de l'assembly.|  
|`-t[p] infile`|Affiche le jeton de la clé publique stockée dans *infile*. Le contenu d’*infile* doit être une clé publique générée précédemment à partir d’un fichier de paire de clés à l’aide de  **-p**.  N’utilisez pas l’option **-t[p]** pour extraire directement le jeton d’un fichier de paire de clés.<br /><br /> Sn.exe calcule le jeton à l'aide d'une fonction de hachage issue de la clé publique. Pour gagner de la place, le Common Language Runtime stocke les jetons des clés publiques dans le manifeste en cas de référence à un autre assembly, lorsqu'il enregistre une dépendance dans un assembly portant un nom fort. L’option **-TP** affiche la clé publique en plus du jeton. Si l'attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> a été appliqué à l'assembly, le jeton est pour la clé d'identité, et le nom d'algorithme de hachage et de la clé d'identité s'affiche.<br /><br /> Notez que cette option ne vérifie pas la signature de l'assembly et qu'elle ne doit pas être utilisée pour prendre des décisions en matière d'approbation.  Cette option affiche seulement les données brutes de jetons de clés publiques.|  
|`-T[p] assembly`|Affiche le jeton de clé publique de l’*assembly*. L’*assembly* doit être le nom d’un fichier qui contient un manifeste d’assembly.<br /><br /> Sn.exe calcule le jeton à l'aide d'une fonction de hachage issue de la clé publique. Pour gagner de la place, le runtime stocke les jetons des clés publiques dans le manifeste en cas de référence à un autre assembly, lorsqu'il enregistre une dépendance dans un assembly portant un nom fort. L’option **-Tp** affiche la clé publique en plus du jeton. Si l'attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> a été appliqué à l'assembly, le jeton est pour la clé d'identité, et le nom d'algorithme de hachage et de la clé d'identité s'affiche.<br /><br /> Notez que cette option ne vérifie pas la signature de l'assembly et qu'elle ne doit pas être utilisée pour prendre des décisions en matière d'approbation.  Cette option affiche seulement les données brutes de jetons de clés publiques.|  
|`-TS assembly infile`|Teste la signature de l' *assembly* signé ou partiellement signé avec la paire de clés dans *infile*.|  
|`-TSc assembly container`|Teste la signature de l' *assembly* signé ou partiellement signé avec la paire de clés dans le *conteneur*de conteneurs de clés.|
|`-v assembly`|Vérifie le nom fort figurant dans *assembly*, où *assembly* est le nom d’un fichier contenant un manifeste d’assembly.|  
|`-vf assembly`|Vérifie le nom fort dans *assembly*. Contrairement à l’option **-v**, **-vf** force la vérification même si celle-ci a été désactivée à l’aide de l’option **-Vr**.|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Crée un fichier des entrées d'inscription (.reg) que vous pouvez utiliser pour inscrire l'assembly spécifié afin d'ignorer la vérification. Les règles d’affectation des noms d’assemblys qui s’appliquent à l’option **-Vr** s’appliquent également à **-Vk**. Pour plus d’informations sur les options *userlist* et *infile*, consultez l’option **-Vr**.|  
|`-Vl`|Répertorie les paramètres actuels de la vérification des noms forts sur cet ordinateur.|  
|`-Vr  assembly [userlist] [infile]`|Inscrit l’*assembly* pour que la vérification soit ignorée. Éventuellement, vous pouvez spécifier une liste de noms d'utilisateurs séparés par une virgule à laquelle l'exception de vérification s'appliquera. Si vous spécifiez *infile*, la vérification reste activée, mais la clé publique figurant dans *infile* est utilisée pendant les opérations de vérification. Vous pouvez spécifier *assembly* sous la forme *\*, strongname* pour inscrire tous les assemblys avec le nom fort spécifié. Pour *strongname*, spécifiez la chaîne de chiffres hexadécimaux représentant la clé publique sous forme de jetons. Consultez les options **-t** et **-T** pour afficher le jeton de clé publique. **Attention :** Utilisez cette option uniquement pendant le développement. L'ajout d'un assembly à la liste des omissions de vérification crée une faille de sécurité. Un assembly malveillant peut utiliser le nom complètement spécifié (nom, version, culture et jeton de clé publique) de l'assembly ajouté à la liste des omissions de vérification pour usurper son identité. Cela permet également à l'assembly malveillant d'ignorer la vérification.|  
|||  
|`-Vu  assembly`|Annule l’inscription de l’*assembly* pour que la vérification soit ignorée. Les mêmes règles d’affectation de noms aux assemblys s’appliquent aux options **-Vr** et **-Vu**.|  
|`-Vx`|Supprime toutes les entrées concernées par l'exception de vérification.|  
|`-?`|Affiche la syntaxe et les options de commande de l'outil.|  
  
> [!NOTE]
> Toutes les options de Sn.exe respectent la casse et doivent être tapées exactement comme indiqué pour pouvoir être reconnues par l'outil.  
  
## <a name="remarks"></a>Remarques  
 Les options **-R** et **-Rc** sont utiles avec les assemblys dont la signature a été différée. Dans ce cas, seule la clé publique est définie au moment de la compilation et la signature a lieu par la suite, lorsque la clé privée est connue.  
  
> [!NOTE]
> Pour les paramètres (par exemple, **-Vr**) qui écrivent dans les ressources protégées, telles que le Registre, exécutez SN.exe comme administrateur.  
  
L’outil Strong Name suppose que les paires de clés publiques/privées sont générées avec l’identificateur d’algorithme `AT_SIGNATURE`. Les paires de clés publiques/privées générées avec l’algorithme `AT_KEYEXCHANGE` génèrent une erreur.

## <a name="examples"></a>Exemples  
 La commande suivante crée une nouvelle paire de clés aléatoire et la stocke dans `keyPair.snk`.  
  
```console  
sn -k keyPair.snk  
```  
  
 La commande suivante stocke la clé figurant dans `keyPair.snk` dans le conteneur `MyContainer` du fournisseur de services de chiffrement de noms forts.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 La commande suivante extrait la clé publique de `keyPair.snk` et la stocke dans `publicKey.snk`.  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 La commande suivante affiche la clé publique et le jeton pour la clé publique contenue dans `publicKey.snk`.  
  
```console  
sn -tp publicKey.snk  
```  
  
 La commande suivante vérifie l'assembly `MyAsm.dll`.  
  
```console  
sn -v MyAsm.dll  
```  
  
 La commande suivante supprime `MyContainer` du fournisseur de services de chiffrement par défaut.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Al.exe (Assembly Linker)](al-exe-assembly-linker.md)
- [Assemblys avec nom fort](../../standard/assembly/strong-named.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
