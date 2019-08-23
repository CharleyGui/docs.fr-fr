---
title: Schéma des paramètres de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927629"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="b6fb2-102">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b6fb2-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="b6fb2-103">Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="b6fb2-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="b6fb2-105"> **\<mscorlib>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="b6fb2-106"> **\<cryptographySettings>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="b6fb2-107"> **\<cryptoNameMapping>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="b6fb2-108"> **\<cryptoClasses>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="b6fb2-109"> **\<cryptoClass>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="b6fb2-110"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="b6fb2-111"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="b6fb2-112"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="b6fb2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b6fb2-113">Element</span></span>|<span data-ttu-id="b6fb2-114">Description</span><span class="sxs-lookup"><span data-stu-id="b6fb2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6fb2-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="b6fb2-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="b6fb2-116">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="b6fb2-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b6fb2-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="b6fb2-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="b6fb2-118">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="b6fb2-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b6fb2-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="b6fb2-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="b6fb2-120">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="b6fb2-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="b6fb2-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="b6fb2-122">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b6fb2-123"> **\<mscorlib>** , élément pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b6fb2-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="b6fb2-124">Contient l’élément **\<cryptographySettings>** .</span><span class="sxs-lookup"><span data-stu-id="b6fb2-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="b6fb2-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="b6fb2-126">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="b6fb2-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="b6fb2-128">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="b6fb2-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="b6fb2-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="b6fb2-130">Contient les mappages d’OID ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="b6fb2-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6fb2-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6fb2-131">See also</span></span>

- [<span data-ttu-id="b6fb2-132">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b6fb2-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b6fb2-133">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b6fb2-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
