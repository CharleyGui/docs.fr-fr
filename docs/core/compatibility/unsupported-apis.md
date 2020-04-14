---
title: API non pris en œtté sur .NET Core
titleSuffix: ''
description: Apprenez quelles API du cadre .NET qui jettent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242944"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>API qui jettent toujours des exceptions sur .NET Core

Les API suivantes jetteront toujours un <xref:System.PlatformNotSupportedException> noyau sur .NET sur tout ou un sous-ensemble de plates-formes.

Cet article organise les membres concernés de l’API par espace de nom.

> [!NOTE]
>
> - Cet article est un travail en cours. Ce n’est pas une liste complète d’API qui jettent des exceptions sur .NET Core.
> - Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui jettent sur .NET Core. Pour plus d’informations, voir [la sérialisation binaire dans .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>Système

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Tous |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Tous |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Tous |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Tous |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Tous |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Tous |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Compiler

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Tous |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Tous |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Tous |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Tous |

## <a name="systemconfiguration"></a>System.Configuration

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(tous les membres) | Tous |

## <a name="systemconsole"></a>System.Console

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType>(obtenir seulement) | Linux et macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Console.Title?displayProperty=nameWithType>(obtenir seulement) | Linux et macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |

## <a name="systemdatacommon"></a>System.Data.Common

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(jette <xref:System.NotSupportedException>) | Tous |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(réglé uniquement) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(réglé uniquement) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(obtenir seulement) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |

## <a name="systemio"></a>System.IO

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |

## <a name="systemiopipes"></a>System.IO.Pipes

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(réglé uniquement) | Linux et macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux et macOS |

## <a name="systemmedia"></a>System.Médias

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |

## <a name="systemnet"></a>System.Net

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Tous |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System.Net.Sockets

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Tous |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Tous |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Tous |

## <a name="systemreflection"></a>System.Reflection

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Tous |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Tous |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Tous |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Tous |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Tous |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Tous |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Tous |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Tous |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Tous |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux et macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Tous |

## <a name="systemsecurity"></a>System.Security

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Tous |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Tous |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Tous |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Tous |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Tous |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | Tous |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Tous |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux et macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tous |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Tous |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Tous |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certificates

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(réglé uniquement) | Tous |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |

## <a name="systemsecuritypolicy"></a>System.security.policy

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tous |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Tous |

## <a name="systemthreading"></a>System.Threading

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tous |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Tous |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Tous |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Tous |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Tous |

## <a name="systemxml"></a>System.Xml

| Membre | Plates-formes qui jettent |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Tous |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Tous |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Tous |

## <a name="see-also"></a>Voir aussi

- [Breaking changes for migration from .NET Framework to .NET Core](../compatibility/fx-core.md)
- [Sérialisation binaire dans .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md)
