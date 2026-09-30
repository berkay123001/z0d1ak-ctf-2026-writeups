# Salvage Protocol · Pwn

**Core idea:** a bytecode VM restricted the request *types* it could send, but not the bytes placed inside a request body. The downstream vault parsed those bytes as further framed requests.

## Two trust boundaries

The externally reachable `reclaimd` VM talked to a local `vaultd`. The VM could normally issue only safe operations; the sealed `vault/flag` record was not listed. The vault protocol itself used a four-byte big-endian length followed by a request with a type, a name, and a data field. A vault loop could process several requests on one connection.

Reverse engineering showed a second weakness in the vault. One branch of its clearance check compared the requested record index against a caller-influenced buffer instead of comparing the random token. The flag was record index `5`. The protected operation could therefore be made to accept a predictable value, provided we could reach the vault's type-3 operation.

## The chain

The VM could not produce type 3 directly. It *could* produce a type-2 request containing arbitrary data. By encoding two complete vault frames inside that data—first a type-3 request for `vault/flag` with clearance `5`, then a type-2 fetch—the downstream frame parser processed operations the VM itself would never authorize. Individual bytes had to be appended with the VM's `0x11` operation; its bulk-write operation reset the state used for this path.

The exploit is a parser-boundary failure, not a guess of the random token. It also illustrates why testing `vaultd` directly is insufficient: the real win required the complete `reclaimd → vaultd` path.

## Evidence and limits

The archived record includes a local test against the vault and a live remote flag through the VM-facing service.

**Flag:** `zdk{5alvag3d_7hr0u6h_tHE_53aM}`
