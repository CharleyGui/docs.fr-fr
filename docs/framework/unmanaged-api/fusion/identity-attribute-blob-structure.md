---
title: IDENTITY_ATTRIBUTE_BLOB, structure
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e478cb89821ce8666f1746e752e06d2caa3ad2bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751592"
---
# <a name="identityattributeblob-structure"></a><span data-ttu-id="18ff7-102">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="18ff7-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>
<span data-ttu-id="18ff7-103">Contient des informations sur un seul attribut dans un assembly et se compose de trois `DWORD`s.</span><span class="sxs-lookup"><span data-stu-id="18ff7-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="18ff7-104">Chaque `DWORD` est un offset dans une mémoire tampon de caractères produit par le `CurrentIntoBuffer` méthode de la [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) interface</span><span class="sxs-lookup"><span data-stu-id="18ff7-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ff7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18ff7-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="18ff7-106">Membres</span><span class="sxs-lookup"><span data-stu-id="18ff7-106">Members</span></span>  
  
|<span data-ttu-id="18ff7-107">Membre</span><span class="sxs-lookup"><span data-stu-id="18ff7-107">Member</span></span>|<span data-ttu-id="18ff7-108">Description</span><span class="sxs-lookup"><span data-stu-id="18ff7-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="18ff7-109">Le premier offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="18ff7-109">The first offset into the character buffer.</span></span> <span data-ttu-id="18ff7-110">Ce décalage n’est pas suivi par espace de noms de l’attribut, mais par une série de caractères null.</span><span class="sxs-lookup"><span data-stu-id="18ff7-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="18ff7-111">Par conséquent, il n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="18ff7-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="18ff7-112">Deuxième offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="18ff7-112">The second offset into the character buffer.</span></span> <span data-ttu-id="18ff7-113">Cet emplacement marque le début du nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="18ff7-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="18ff7-114">Troisième offset dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="18ff7-114">The third offset into the character buffer.</span></span> <span data-ttu-id="18ff7-115">Cet emplacement marque le début de la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="18ff7-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="18ff7-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="18ff7-116">Sample</span></span>  
 <span data-ttu-id="18ff7-117">L’exemple suivant illustre plusieurs étapes de base, ce qui finalement entraînent un remplis `IDENTITY_ATTRIBUTE_BLOB` structure :</span><span class="sxs-lookup"><span data-stu-id="18ff7-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="18ff7-118">Obtenir un [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="18ff7-118">Obtain an [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="18ff7-119">Appelez le `IReferenceIdentity::EnumAttributes` (méthode) et obtenir un [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).</span><span class="sxs-lookup"><span data-stu-id="18ff7-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="18ff7-120">Créer une mémoire tampon de caractères et effectuer un cast en tant qu’un `IDENTITY_ATTRIBUTE_BLOB` structure.</span><span class="sxs-lookup"><span data-stu-id="18ff7-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="18ff7-121">Appelez le `CurrentIntoBuffer` méthode de la `IEnumIDENTITY_ATTRIBUTE` interface.</span><span class="sxs-lookup"><span data-stu-id="18ff7-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="18ff7-122">Cette méthode copie les attributs `Namespace`, `Name`, et `Value` dans la mémoire tampon de caractères.</span><span class="sxs-lookup"><span data-stu-id="18ff7-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="18ff7-123">Les trois offsets de ces chaînes seront disponibles dans le `IDENTITY_ATTRIBUTE_BLOB` structure.</span><span class="sxs-lookup"><span data-stu-id="18ff7-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="18ff7-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="18ff7-124">To run the sample</span></span>  
 <span data-ttu-id="18ff7-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="18ff7-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="18ff7-126">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="18ff7-126">Sample output</span></span>  
 <span data-ttu-id="18ff7-127">Culture = neutral</span><span class="sxs-lookup"><span data-stu-id="18ff7-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="18ff7-128">Nom = système</span><span class="sxs-lookup"><span data-stu-id="18ff7-128">name = System</span></span>  
  
 <span data-ttu-id="18ff7-129">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="18ff7-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="18ff7-130">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="18ff7-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="18ff7-131">Version = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="18ff7-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ff7-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18ff7-132">Requirements</span></span>  
 <span data-ttu-id="18ff7-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18ff7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ff7-134">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="18ff7-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="18ff7-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18ff7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ff7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18ff7-136">See also</span></span>

- [<span data-ttu-id="18ff7-137">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="18ff7-137">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
- [<span data-ttu-id="18ff7-138">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="18ff7-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
- [<span data-ttu-id="18ff7-139">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="18ff7-139">IDENTITY_ATTRIBUTE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-structure.md)
- [<span data-ttu-id="18ff7-140">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="18ff7-140">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
