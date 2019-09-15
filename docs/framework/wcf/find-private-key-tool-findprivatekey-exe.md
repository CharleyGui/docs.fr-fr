---
title: Outil de recherche de clé privée (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990353"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="906de-102">Outil de recherche de clé privée (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="906de-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="906de-103">Cet outil de ligne de commande peut être utilisé pour récupérer une clé privée provenant d'un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="906de-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="906de-104">Par exemple, *FindPrivateKey. exe* peut être utilisé pour Rechercher l’emplacement et le nom du fichier de clé privée associé à un certificat X. 509 spécifique dans le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="906de-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="906de-105">L'outil FindPrivateKey est fourni à titre d'exemple WCF.</span><span class="sxs-lookup"><span data-stu-id="906de-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="906de-106">Pour plus d’informations sur l’emplacement de l’exemple et sur la façon de le générer, consultez [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="906de-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="906de-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="906de-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="906de-108">Notes</span><span class="sxs-lookup"><span data-stu-id="906de-108">Remarks</span></span>

<span data-ttu-id="906de-109">Les tables suivantes décrivent les arguments et les options qui peuvent être utilisés avec l'outil de recherche de clé privée Clé (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="906de-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="906de-110">Argument</span><span class="sxs-lookup"><span data-stu-id="906de-110">Argument</span></span>|<span data-ttu-id="906de-111">Description</span><span class="sxs-lookup"><span data-stu-id="906de-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="906de-112">Nom du magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="906de-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="906de-113">Emplacement du magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="906de-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="906de-114">Option</span><span class="sxs-lookup"><span data-stu-id="906de-114">Option</span></span>|<span data-ttu-id="906de-115">Description</span><span class="sxs-lookup"><span data-stu-id="906de-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="906de-116">`/n <` *subjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="906de-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="906de-117">Spécifie le nom du sujet du certificat.</span><span class="sxs-lookup"><span data-stu-id="906de-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="906de-118">`/t <` *thumbprint* `>`</span><span class="sxs-lookup"><span data-stu-id="906de-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="906de-119">Spécifie l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="906de-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="906de-120">Utilisez Certmgr.exe pour récupérer l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="906de-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="906de-121">Affiche le nom de fichier uniquement.</span><span class="sxs-lookup"><span data-stu-id="906de-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="906de-122">Affiche le répertoire uniquement.</span><span class="sxs-lookup"><span data-stu-id="906de-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="906de-123">Affiche le nom de fichier absolu.</span><span class="sxs-lookup"><span data-stu-id="906de-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="906de-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="906de-124">Examples</span></span>

<span data-ttu-id="906de-125">La commande suivante récupère la clé privée pour John Doe :</span><span class="sxs-lookup"><span data-stu-id="906de-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="906de-126">La commande suivante récupère la clé privée pour l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="906de-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
