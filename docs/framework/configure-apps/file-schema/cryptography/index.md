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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088008"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="5d759-102">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5d759-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="5d759-103">Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5d759-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
<span data-ttu-id="5d759-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d759-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d759-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5d759-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="5d759-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings**](cryptographysettings-element.md) ></span><span class="sxs-lookup"><span data-stu-id="5d759-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="5d759-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoNameMapping**](cryptonamemapping-element.md) ></span><span class="sxs-lookup"><span data-stu-id="5d759-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="5d759-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses**](cryptoclasses-element.md) ></span><span class="sxs-lookup"><span data-stu-id="5d759-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="5d759-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d759-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>\
<span data-ttu-id="5d759-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<élément nameEntry**](nameentry-element.md) ></span><span class="sxs-lookup"><span data-stu-id="5d759-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>\
<span data-ttu-id="5d759-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**oidMap**](oidmap-element.md) ></span><span class="sxs-lookup"><span data-stu-id="5d759-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="5d759-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d759-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>

|<span data-ttu-id="5d759-113">Élément</span><span class="sxs-lookup"><span data-stu-id="5d759-113">Element</span></span>|<span data-ttu-id="5d759-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d759-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d759-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="5d759-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="5d759-116">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="5d759-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="5d759-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="5d759-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="5d759-118">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="5d759-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="5d759-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="5d759-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="5d759-120">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="5d759-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="5d759-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="5d759-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="5d759-122">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="5d759-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="5d759-123"> **\<mscorlib>** , élément pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5d759-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="5d759-124">Contient l’élément **\<cryptographySettings>** .</span><span class="sxs-lookup"><span data-stu-id="5d759-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="5d759-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="5d759-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="5d759-126">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="5d759-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="5d759-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="5d759-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="5d759-128">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="5d759-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="5d759-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="5d759-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="5d759-130">Contient les mappages d’OID ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="5d759-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d759-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d759-131">See also</span></span>

- [<span data-ttu-id="5d759-132">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5d759-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d759-133">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="5d759-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
