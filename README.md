# Removing `Org2MSP` via `configtxlator`

First signing via `configtxlator` and then submitting via `peer channel update` (bug fixed after discussing with `@jyellick` in `chat.hyperledger.com`)

Logs as below:

```
2017-06-11 02:15:50.264 UTC [policies] ProposePolicy -> DEBU e23 Proposed new policy Readers for Orderer
2017-06-11 02:15:50.264 UTC [policies] ProposePolicy -> DEBU e25 Proposed new policy Writers for Orderer
2017-06-11 02:15:50.264 UTC [common/config] NewStandardValues -> DEBU e26 Initializing protos for *config.OrganizationProtos
2017-06-11 02:15:50.264 UTC [common/config] initializeProtosStruct -> DEBU e27 Processing field: MSP
2017-06-11 02:15:50.264 UTC [policies] ProposePolicy -> DEBU e28 Proposed new policy Readers for OrdererOrg
2017-06-11 02:15:50.264 UTC [policies] ProposePolicy -> DEBU e29 Proposed new policy Writers for OrdererOrg
2017-06-11 02:15:50.264 UTC [policies] ProposePolicy -> DEBU e2a Proposed new policy Admins for OrdererOrg
2017-06-11 02:15:50.264 UTC [common/config] Validate -> DEBU e2b Anchor peers for org Org1MSP are anchor_peers:<host:"peer0.org1.example.com" port:7051 > 
2017-06-11 02:15:50.264 UTC [common/config] validateMSP -> DEBU e2c Setting up MSP for org Org1MSP
2017-06-11 02:15:50.265 UTC [msp] NewBccspMsp -> DEBU e2d Creating BCCSP-based MSP instance
2017-06-11 02:15:50.265 UTC [msp] Setup -> DEBU e2e Setting up MSP instance Org1MSP
2017-06-11 02:15:50.265 UTC [msp/identity] newIdentity -> DEBU e2f Creating identity instance for ID &{Org1MSP b50e0838cb88988058fb0fc5e0d5ed9cbba35b3d414eb30bfd7f21e5f7e0c044}
2017-06-11 02:15:50.265 UTC [msp/identity] newIdentity -> DEBU e30 Creating identity instance for ID &{Org1MSP b04f8fff7c94a6917d031c1359dea17e68eb12dc54ffc87f4a69e33bce2cfd62}
2017-06-11 02:15:50.266 UTC [common/config] validateMSP -> DEBU e31 Setting up MSP for org OrdererOrg
2017-06-11 02:15:50.266 UTC [msp] NewBccspMsp -> DEBU e32 Creating BCCSP-based MSP instance
2017-06-11 02:15:50.266 UTC [msp] Setup -> DEBU e33 Setting up MSP instance OrdererMSP
2017-06-11 02:15:50.266 UTC [msp/identity] newIdentity -> DEBU e34 Creating identity instance for ID &{OrdererMSP e9f5e655b9215dc17caf5acf818862a674d5397c4054947110c0fcf9e4873857}
2017-06-11 02:15:50.266 UTC [msp/identity] newIdentity -> DEBU e35 Creating identity instance for ID &{OrdererMSP 2933ca3408e22f2600a3b260d9d5f36294c54e19c28e2beffb20df42e869dabb}
2017-06-11 02:15:50.266 UTC [msp] Setup -> DEBU e36 Setting up the MSP manager (2 msps)
2017-06-11 02:15:50.267 UTC [msp] Setup -> DEBU e37 MSP manager setup complete, setup 2 msps
2017-06-11 02:15:50.267 UTC [orderer/common/blockcutter] Ordered -> DEBU e38 Found message which requested to be isolated, cutting into its own batch
2017-06-11 02:15:50.267 UTC [fsblkstorage] retrieveBlockByNumber -> DEBU e39 retrieveBlockByNumber() - blockNum = [4]
2017-06-11 02:15:50.267 UTC [fsblkstorage] newBlockfileStream -> DEBU e3a newBlockfileStream(): filePath=[/var/hyperledger/production/orderer/chains/mychannel/blockfile_000000], startOffset=[38224]
2017-06-11 02:15:50.267 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU e3b Remaining bytes=[4976], Going to peek [8] bytes
2017-06-11 02:15:50.267 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU e3c Returning blockbytes - length=[4974], placementInfo={fileNum=[0], startOffset=[38224], bytesOffset=[38226]}
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e3d Adding to config map: [Groups] /Channel
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e3e Adding to config map: [Groups] /Channel/Application
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e3f Adding to config map: [Groups] /Channel/Application/Org2MSP
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e40 Adding to config map: [Groups] /Channel/Application/Org1MSP
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e41 Adding to config map: [Policy] /Channel/Application/Admins
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e42 Adding to config map: [Policy] /Channel/Application/Readers
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e43 Adding to config map: [Policy] /Channel/Application/Writers
2017-06-11 02:15:50.267 UTC [common/configtx] addToMap -> DEBU e44 Adding to config map: [Groups] /Channel
2017-06-11 02:15:50.268 UTC [common/configtx] addToMap -> DEBU e45 Adding to config map: [Groups] /Channel/Application
2017-06-11 02:15:50.268 UTC [common/configtx] addToMap -> DEBU e46 Adding to config map: [Groups] /Channel/Application/Org1MSP
2017-06-11 02:15:50.268 UTC [common/configtx] addToMap -> DEBU e47 Adding to config map: [Policy] /Channel/Application/Admins
2017-06-11 02:15:50.268 UTC [common/configtx] addToMap -> DEBU e48 Adding to config map: [Policy] /Channel/Application/Readers
2017-06-11 02:15:50.268 UTC [common/configtx] addToMap -> DEBU e49 Adding to config map: [Policy] /Channel/Application/Writers
2017-06-11 02:15:50.268 UTC [policies] GetPolicy -> DEBU e4a Returning policy Admins for evaluation
2017-06-11 02:15:50.268 UTC [cauthdsl] func1 -> DEBU e4b Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:15:50.268 UTC [cauthdsl] func2 -> DEBU e4c Principal evaluation starts: (&{0}) (used [false false])
2017-06-11 02:15:50.268 UTC [msp/identity] newIdentity -> DEBU e4d Creating identity instance for ID &{Org2MSP a2da0f93eae359036176a3d541791c404daf75702315a7546bf09e1ac617b48d}
2017-06-11 02:15:50.268 UTC [cauthdsl] func2 -> DEBU e4e Identity ([10 7 79 114 103 50 77 83 80 18 156 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 76 106 67 67 65 100 87 103 65 119 73 66 65 103 73 82 65 77 54 90 77 104 118 43 104 87 115 87 85 102 110 98 98 83 118 50 75 55 99 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 119 119 87 81 87 82 116 97 87 53 65 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 76 99 76 76 108 105 90 66 54 81 47 81 51 108 75 78 86 120 90 100 66 43 110 53 75 70 108 53 100 109 74 10 85 53 108 101 71 89 116 109 100 67 47 73 81 68 53 56 43 116 106 117 50 65 83 109 67 54 47 56 97 114 108 87 116 102 85 67 68 72 73 51 98 82 97 85 81 76 121 57 109 76 49 116 87 118 43 106 89 106 66 103 77 65 52 71 10 65 49 85 100 68 119 69 66 47 119 81 69 65 119 73 70 111 68 65 84 66 103 78 86 72 83 85 69 68 68 65 75 66 103 103 114 66 103 69 70 66 81 99 68 65 84 65 77 66 103 78 86 72 82 77 66 65 102 56 69 65 106 65 65 10 77 67 115 71 65 49 85 100 73 119 81 107 77 67 75 65 73 66 80 118 113 43 122 90 53 50 115 117 113 68 81 107 119 113 114 75 100 52 66 80 74 78 99 116 99 48 122 57 77 116 72 47 69 48 74 50 48 89 113 53 77 65 111 71 10 67 67 113 71 83 77 52 57 66 65 77 67 65 48 99 65 77 69 81 67 73 66 86 78 122 52 67 115 97 99 97 107 55 82 106 82 110 115 73 109 65 111 107 57 53 66 84 79 82 48 104 84 72 70 106 108 75 80 80 104 47 71 103 103 10 65 105 65 70 53 85 122 48 109 97 53 51 87 48 50 83 111 73 65 89 68 100 52 101 114 115 113 49 79 99 73 72 54 122 79 118 50 43 114 88 66 109 77 111 71 119 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]) does not satisfy principal: The identity is a member of a different MSP (expected Org1MSP, got Org2MSP)
2017-06-11 02:15:50.268 UTC [msp/identity] newIdentity -> DEBU e4f Creating identity instance for ID &{Org1MSP b04f8fff7c94a6917d031c1359dea17e68eb12dc54ffc87f4a69e33bce2cfd62}
2017-06-11 02:15:50.269 UTC [msp] SatisfiesPrincipal -> DEBU e50 Checking if identity satisfies ADMIN role for Org1MSP

2017-06-11 02:15:50.269 UTC [cauthdsl] func2 -> DEBU e51 Principal matched by identity: (&{0}) for [10 7 79 114 103 49 77 83 80 18 156 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 76 122 67 67 65 100 87 103 65 119 73 66 65 103 73 82 65 73 103 98 89 98 74 103 105 104 108 71 52 101 76 103 119 98 73 43 110 87 107 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 69 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 69 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 119 119 87 81 87 82 116 97 87 53 65 98 51 74 110 77 83 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 69 80 78 87 88 100 98 85 80 107 108 79 117 81 112 99 89 82 108 119 69 43 110 84 86 99 49 56 69 115 66 10 103 70 50 118 89 88 52 106 114 107 106 105 53 74 55 49 78 70 114 84 53 78 113 87 118 67 81 43 83 108 80 120 118 66 118 52 104 99 54 57 47 50 118 114 103 76 104 57 66 88 76 88 50 53 50 106 89 106 66 103 77 65 52 71 10 65 49 85 100 68 119 69 66 47 119 81 69 65 119 73 70 111 68 65 84 66 103 78 86 72 83 85 69 68 68 65 75 66 103 103 114 66 103 69 70 66 81 99 68 65 84 65 77 66 103 78 86 72 82 77 66 65 102 56 69 65 106 65 65 10 77 67 115 71 65 49 85 100 73 119 81 107 77 67 75 65 73 71 112 69 89 112 65 87 69 75 69 47 57 49 105 66 99 100 51 117 50 102 75 43 54 74 82 114 43 66 99 89 108 66 80 89 103 83 99 83 52 100 119 107 77 65 111 71 10 67 67 113 71 83 77 52 57 66 65 77 67 65 48 103 65 77 69 85 67 73 81 68 71 104 115 97 111 103 53 119 76 68 74 43 104 112 43 107 51 83 69 51 98 114 102 115 77 49 79 116 112 53 81 87 71 47 108 112 80 69 97 106 99 10 50 81 73 103 81 49 109 66 115 49 78 110 72 54 101 54 79 52 111 108 115 110 122 51 71 65 114 51 110 55 115 52 66 122 43 78 71 65 88 104 74 114 49 66 48 68 119 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:15:50.269 UTC [msp/identity] Verify -> DEBU e52 Verify: digest = 00000000  b5 b8 0c 7e 79 4a a9 5e  1d 89 fa 5f 8f 2d bf b6  |...~yJ.^..._.-..|
00000010  46 ec 1f 8e 53 d7 9d 06  a3 fe ef aa 47 c1 2f 47  |F...S.......G./G|
2017-06-11 02:15:50.269 UTC [msp/identity] Verify -> DEBU e53 Verify: sig = 00000000  30 44 02 20 3c 7b 2d b5  35 e4 84 57 f3 9d 41 56  |0D. <{-.5..W..AV|
00000010  5d 31 be 06 a9 9c 46 e3  9b b5 1e 0b ed d0 e8 73  |]1....F........s|
00000020  91 d6 c8 a3 02 20 70 66  26 07 fa eb b1 a6 30 a1  |..... pf&.....0.|
00000030  f9 42 b2 6d 6f 1d 63 a1  06 e3 5a 60 53 c9 ae 9d  |.B.mo.c...Z`S...|
00000040  64 04 31 7d 52 b8                                 |d.1}R.|
2017-06-11 02:15:50.269 UTC [cauthdsl] func2 -> DEBU e54 Principal evaluation succeeds: (&{0}) (used [false false])
2017-06-11 02:15:50.269 UTC [cauthdsl] func1 -> DEBU e55 Gate evaluation succeeds: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:15:50.269 UTC [cauthdsl] func1 -> DEBU e56 Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:15:50.269 UTC [cauthdsl] func2 -> DEBU e57 Principal evaluation starts: (&{0}) (used [false false])
2017-06-11 02:15:50.269 UTC [msp/identity] newIdentity -> DEBU e58 Creating identity instance for ID &{Org2MSP a2da0f93eae359036176a3d541791c404daf75702315a7546bf09e1ac617b48d}
2017-06-11 02:15:50.269 UTC [msp] SatisfiesPrincipal -> DEBU e59 Checking if identity satisfies ADMIN role for Org2MSP

2017-06-11 02:15:50.269 UTC [cauthdsl] func2 -> DEBU e5a Principal matched by identity: (&{0}) for [10 7 79 114 103 50 77 83 80 18 156 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 76 106 67 67 65 100 87 103 65 119 73 66 65 103 73 82 65 77 54 90 77 104 118 43 104 87 115 87 85 102 110 98 98 83 118 50 75 55 99 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 119 119 87 81 87 82 116 97 87 53 65 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 76 99 76 76 108 105 90 66 54 81 47 81 51 108 75 78 86 120 90 100 66 43 110 53 75 70 108 53 100 109 74 10 85 53 108 101 71 89 116 109 100 67 47 73 81 68 53 56 43 116 106 117 50 65 83 109 67 54 47 56 97 114 108 87 116 102 85 67 68 72 73 51 98 82 97 85 81 76 121 57 109 76 49 116 87 118 43 106 89 106 66 103 77 65 52 71 10 65 49 85 100 68 119 69 66 47 119 81 69 65 119 73 70 111 68 65 84 66 103 78 86 72 83 85 69 68 68 65 75 66 103 103 114 66 103 69 70 66 81 99 68 65 84 65 77 66 103 78 86 72 82 77 66 65 102 56 69 65 106 65 65 10 77 67 115 71 65 49 85 100 73 119 81 107 77 67 75 65 73 66 80 118 113 43 122 90 53 50 115 117 113 68 81 107 119 113 114 75 100 52 66 80 74 78 99 116 99 48 122 57 77 116 72 47 69 48 74 50 48 89 113 53 77 65 111 71 10 67 67 113 71 83 77 52 57 66 65 77 67 65 48 99 65 77 69 81 67 73 66 86 78 122 52 67 115 97 99 97 107 55 82 106 82 110 115 73 109 65 111 107 57 53 66 84 79 82 48 104 84 72 70 106 108 75 80 80 104 47 71 103 103 10 65 105 65 70 53 85 122 48 109 97 53 51 87 48 50 83 111 73 65 89 68 100 52 101 114 115 113 49 79 99 73 72 54 122 79 118 50 43 114 88 66 109 77 111 71 119 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:15:50.270 UTC [msp/identity] Verify -> DEBU e5b Verify: digest = 00000000  5a cf 4c 08 e0 c4 b3 b8  f6 24 1e f1 3d a3 f7 67  |Z.L......$..=..g|
00000010  ec d8 c5 82 5d 87 a6 ea  cc 17 38 80 c7 c2 59 75  |....].....8...Yu|
2017-06-11 02:15:50.270 UTC [msp/identity] Verify -> DEBU e5c Verify: sig = 00000000  30 45 02 21 00 d2 ac d1  8b ea 71 79 74 dc f0 ab  |0E.!......qyt...|
00000010  0a fa 86 16 6a 46 c5 f2  28 32 3f 3b 1f af cd 13  |....jF..(2?;....|
00000020  73 bc 09 d0 57 02 20 79  70 79 c4 44 de 4a d9 00  |s...W. ypy.D.J..|
00000030  5d d9 91 59 3d 12 8b 02  fb 0d a7 a3 3c 5d ae d6  |]..Y=.......<]..|
00000040  e2 e6 dd 0f fb a4 9a                              |.......|
2017-06-11 02:15:50.270 UTC [cauthdsl] func2 -> DEBU e5d Principal evaluation succeeds: (&{0}) (used [false false])
2017-06-11 02:15:50.270 UTC [cauthdsl] func1 -> DEBU e5e Gate evaluation succeeds: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:15:50.270 UTC [common/configtx] processConfig -> DEBU e5f Beginning new config for channel mychannel
2017-06-11 02:15:50.270 UTC [common/config] NewStandardValues -> DEBU e60 Initializing protos for *config.ChannelProtos
2017-06-11 02:15:50.270 UTC [common/config] initializeProtosStruct -> DEBU e61 Processing field: HashingAlgorithm
2017-06-11 02:15:50.270 UTC [common/config] initializeProtosStruct -> DEBU e62 Processing field: BlockDataHashingStructure
2017-06-11 02:15:50.270 UTC [common/config] initializeProtosStruct -> DEBU e63 Processing field: OrdererAddresses
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e64 Processing field: Consortium
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e65 Proposed new policy Readers for Channel
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e66 Proposed new policy Writers for Channel
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e67 Proposed new policy Admins for Channel
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e68 Initializing protos for *struct {}
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e69 Proposed new policy Readers for Application
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e6a Proposed new policy Writers for Application
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e6b Proposed new policy Admins for Application
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e6c Initializing protos for *config.OrganizationProtos
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e6d Processing field: MSP
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e6e Initializing protos for *config.ApplicationOrgProtos
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e6f Processing field: AnchorPeers
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e70 Initializing protos for *config.OrganizationProtos
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e71 Processing field: MSP
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e72 Proposed new policy Readers for Org1MSP
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e73 Proposed new policy Writers for Org1MSP
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e74 Proposed new policy Admins for Org1MSP
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e75 Initializing protos for *config.OrdererProtos
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e76 Processing field: ConsensusType
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e77 Processing field: BatchSize
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e78 Processing field: BatchTimeout
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e79 Processing field: KafkaBrokers
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e7a Processing field: ChannelRestrictions
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e7b Proposed new policy BlockValidation for Orderer
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e7c Proposed new policy Readers for Orderer
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e7d Proposed new policy Writers for Orderer
2017-06-11 02:15:50.271 UTC [policies] ProposePolicy -> DEBU e7e Proposed new policy Admins for Orderer
2017-06-11 02:15:50.271 UTC [common/config] NewStandardValues -> DEBU e7f Initializing protos for *config.OrganizationProtos
2017-06-11 02:15:50.271 UTC [common/config] initializeProtosStruct -> DEBU e80 Processing field: MSP
2017-06-11 02:15:50.272 UTC [policies] ProposePolicy -> DEBU e81 Proposed new policy Readers for OrdererOrg
2017-06-11 02:15:50.272 UTC [policies] ProposePolicy -> DEBU e82 Proposed new policy Writers for OrdererOrg
2017-06-11 02:15:50.272 UTC [policies] ProposePolicy -> DEBU e83 Proposed new policy Admins for OrdererOrg
2017-06-11 02:15:50.272 UTC [common/config] Validate -> DEBU e84 Anchor peers for org Org1MSP are anchor_peers:<host:"peer0.org1.example.com" port:7051 > 
2017-06-11 02:15:50.272 UTC [common/config] validateMSP -> DEBU e85 Setting up MSP for org Org1MSP
2017-06-11 02:15:50.272 UTC [msp] NewBccspMsp -> DEBU e86 Creating BCCSP-based MSP instance
2017-06-11 02:15:50.272 UTC [msp] Setup -> DEBU e87 Setting up MSP instance Org1MSP
2017-06-11 02:15:50.272 UTC [msp/identity] newIdentity -> DEBU e88 Creating identity instance for ID &{Org1MSP b50e0838cb88988058fb0fc5e0d5ed9cbba35b3d414eb30bfd7f21e5f7e0c044}
2017-06-11 02:15:50.272 UTC [msp/identity] newIdentity -> DEBU e89 Creating identity instance for ID &{Org1MSP b04f8fff7c94a6917d031c1359dea17e68eb12dc54ffc87f4a69e33bce2cfd62}
2017-06-11 02:15:50.273 UTC [common/config] validateMSP -> DEBU e8a Setting up MSP for org OrdererOrg
2017-06-11 02:15:50.273 UTC [msp] NewBccspMsp -> DEBU e8b Creating BCCSP-based MSP instance
2017-06-11 02:15:50.273 UTC [msp] Setup -> DEBU e8c Setting up MSP instance OrdererMSP
2017-06-11 02:15:50.273 UTC [msp/identity] newIdentity -> DEBU e8d Creating identity instance for ID &{OrdererMSP e9f5e655b9215dc17caf5acf818862a674d5397c4054947110c0fcf9e4873857}
2017-06-11 02:15:50.273 UTC [msp/identity] newIdentity -> DEBU e8e Creating identity instance for ID &{OrdererMSP 2933ca3408e22f2600a3b260d9d5f36294c54e19c28e2beffb20df42e869dabb}
2017-06-11 02:15:50.273 UTC [msp] Setup -> DEBU e8f Setting up the MSP manager (2 msps)
2017-06-11 02:15:50.273 UTC [msp] Setup -> DEBU e90 MSP manager setup complete, setup 2 msps
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e91 Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e92 In commit adding relative sub-policy Org1MSP/Readers to Application
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e93 Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e94 In commit adding relative sub-policy Org1MSP/Writers to Application
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e95 Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e96 In commit adding relative sub-policy Org1MSP/Admins to Application
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e97 Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e98 Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e99 Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e9a Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e9b In commit adding relative sub-policy OrdererOrg/Writers to Orderer
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e9c Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e9d In commit adding relative sub-policy OrdererOrg/Admins to Orderer
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU e9e Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU e9f In commit adding relative sub-policy OrdererOrg/Readers to Orderer
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea0 Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea1 Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea2 Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea3 Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea4 Returning policy Org1MSP/Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU ea5 In commit adding relative sub-policy Application/Org1MSP/Readers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea6 Returning policy Org1MSP/Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU ea7 In commit adding relative sub-policy Application/Org1MSP/Writers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU ea8 Returning policy Org1MSP/Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU ea9 In commit adding relative sub-policy Application/Org1MSP/Admins to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eaa Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU eab In commit adding relative sub-policy Application/Readers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eac Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU ead In commit adding relative sub-policy Application/Writers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eae Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU eaf In commit adding relative sub-policy Application/Admins to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eb0 Returning policy Readers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU eb1 In commit adding relative sub-policy Orderer/Readers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eb2 Returning policy Writers for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU eb3 In commit adding relative sub-policy Orderer/Writers to Channel
2017-06-11 02:15:50.274 UTC [policies] GetPolicy -> DEBU eb4 Returning policy Admins for evaluation
2017-06-11 02:15:50.274 UTC [policies] CommitProposals -> DEBU eb5 In commit adding relative sub-policy Orderer/Admins to Channel
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU eb6 Returning policy OrdererOrg/Writers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU eb7 In commit adding relative sub-policy Orderer/OrdererOrg/Writers to Channel
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU eb8 Returning policy OrdererOrg/Admins for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU eb9 In commit adding relative sub-policy Orderer/OrdererOrg/Admins to Channel
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU eba Returning policy OrdererOrg/Readers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ebb In commit adding relative sub-policy Orderer/OrdererOrg/Readers to Channel
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ebc Returning policy BlockValidation for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ebd In commit adding relative sub-policy Orderer/BlockValidation to Channel
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ebe Returning policy Readers for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ebf Returning policy Readers for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec0 Returning policy Writers for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec1 Returning policy Writers for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec2 Returning policy Admins for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec3 Returning policy Admins for evaluation
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec4 Returning policy Readers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ec5 As expected, current configuration has policy '/Channel/Readers'
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec6 Returning policy Writers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ec7 As expected, current configuration has policy '/Channel/Writers'
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ec8 Returning policy Application/Readers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ec9 As expected, current configuration has policy '/Channel/Application/Readers'
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU eca Returning policy Application/Writers for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ecb As expected, current configuration has policy '/Channel/Application/Writers'
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ecc Returning policy Application/Admins for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ecd As expected, current configuration has policy '/Channel/Application/Admins'
2017-06-11 02:15:50.275 UTC [policies] GetPolicy -> DEBU ece Returning policy Orderer/BlockValidation for evaluation
2017-06-11 02:15:50.275 UTC [policies] CommitProposals -> DEBU ecf As expected, current configuration has policy '/Channel/Orderer/BlockValidation'
2017-06-11 02:15:50.275 UTC [orderer/multichain] addBlockSignature -> DEBU ed0 &{ledgerResources:0xc4201da640 chain:0xc4209888d0 cutter:0xc420349540 filters:0xc4201dab60 signer:0x1262e08 lastConfig:2 lastConfigSeq:3}
2017-06-11 02:15:50.275 UTC [orderer/multichain] addBlockSignature -> DEBU ed1 &{}
2017-06-11 02:15:50.275 UTC [msp] GetLocalMSP -> DEBU ed2 Returning existing local MSP
2017-06-11 02:15:50.275 UTC [msp] GetDefaultSigningIdentity -> DEBU ed3 Obtaining default signing identity
2017-06-11 02:15:50.275 UTC [msp] GetLocalMSP -> DEBU ed4 Returning existing local MSP
2017-06-11 02:15:50.275 UTC [msp] GetDefaultSigningIdentity -> DEBU ed5 Obtaining default signing identity
2017-06-11 02:15:50.275 UTC [msp/identity] Sign -> DEBU ed6 Sign: plaintext: 0AD0060A0A4F7264657265724D535012...4635565FC75C2C71457799E2ADB7D7C0 
2017-06-11 02:15:50.275 UTC [msp/identity] Sign -> DEBU ed7 Sign: digest: AC0C0E07757571CDBE3B0E105BAA57EC9AD91BBA78CF8EBED1398C0557A7EE08 
2017-06-11 02:15:50.275 UTC [orderer/multichain] addLastConfigSignature -> DEBU ed8 [channel: mychannel] Detected lastConfigSeq transitioning from 3 to 4, setting lastConfig from 2 to 5
2017-06-11 02:15:50.275 UTC [msp] GetLocalMSP -> DEBU ed9 Returning existing local MSP
2017-06-11 02:15:50.275 UTC [msp] GetDefaultSigningIdentity -> DEBU eda Obtaining default signing identity
2017-06-11 02:15:50.275 UTC [orderer/multichain] addLastConfigSignature -> DEBU edb [channel: mychannel] About to write block, setting its LAST_CONFIG to 5
2017-06-11 02:15:50.275 UTC [msp] GetLocalMSP -> DEBU edc Returning existing local MSP
2017-06-11 02:15:50.276 UTC [msp] GetDefaultSigningIdentity -> DEBU edd Obtaining default signing identity
2017-06-11 02:15:50.276 UTC [msp/identity] Sign -> DEBU ede Sign: plaintext: 08050AD0060A0A4F7264657265724D53...4635565FC75C2C71457799E2ADB7D7C0 
2017-06-11 02:15:50.276 UTC [msp/identity] Sign -> DEBU edf Sign: digest: 125AFABC80B1435F5F22850F7E5BF568212EEFCFCA2DC8771F155F15E8BD9809 
2017-06-11 02:15:50.282 UTC [fsblkstorage] indexBlock -> DEBU ee0 Indexing block [blockNum=5, blockHash=[]byte{0xaf, 0x6a, 0x71, 0xad, 0xa8, 0x6c, 0xff, 0xee, 0x42, 0xa, 0xea, 0x36, 0x7c, 0x45, 0x80, 0x1b, 0x25, 0x96, 0xd2, 0x19, 0x3a, 0x96, 0xbe, 0xff, 0x24, 0x59, 0x53, 0xe7, 0x51, 0x81, 0xdf, 0x2c} txOffsets=
txId= locPointer=offset=70, bytesLength=8506
]
2017-06-11 02:15:50.282 UTC [fsblkstorage] updateCheckpoint -> DEBU ee1 Broadcasting about update checkpointInfo: latestFileChunkSuffixNum=[0], latestFileChunksize=[53699], isChainEmpty=[false], lastBlockNumber=[5]
2017-06-11 02:15:50.282 UTC [orderer/multichain] WriteBlock -> DEBU ee2 [channel: mychannel] Wrote block 5
2017-06-11 02:15:50.282 UTC [fsblkstorage] retrieveBlockByNumber -> DEBU ee3 retrieveBlockByNumber() - blockNum = [5]
2017-06-11 02:15:50.282 UTC [fsblkstorage] newBlockfileStream -> DEBU ee5 newBlockfileStream(): filePath=[/var/hyperledger/production/orderer/chains/mychannel/blockfile_000000], startOffset=[43200]
2017-06-11 02:15:50.282 UTC [fsblkstorage] retrieveBlockByNumber -> DEBU ee4 retrieveBlockByNumber() - blockNum = [5]
2017-06-11 02:15:50.282 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU ee6 Remaining bytes=[10499], Going to peek [8] bytes
2017-06-11 02:15:50.282 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU ee8 Returning blockbytes - length=[10497], placementInfo={fileNum=[0], startOffset=[43200], bytesOffset=[43202]}
2017-06-11 02:15:50.282 UTC [fsblkstorage] newBlockfileStream -> DEBU ee7 newBlockfileStream(): filePath=[/var/hyperledger/production/orderer/chains/mychannel/blockfile_000000], startOffset=[43200]
2017-06-11 02:15:50.282 UTC [orderer/common/deliver] Handle -> DEBU ee9 Delivering block for (0xc4202f6380) channel: mychannel
2017-06-11 02:15:50.284 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU eea Remaining bytes=[10499], Going to peek [8] bytes
2017-06-11 02:15:50.284 UTC [fsblkstorage] nextBlockBytesAndPlacementInfo -> DEBU eeb Returning blockbytes - length=[10497], placementInfo={fileNum=[0], startOffset=[43200], bytesOffset=[43202]}
2017-06-11 02:15:50.284 UTC [orderer/common/deliver] Handle -> DEBU eec Delivering block for (0xc4208cc7a0) channel: mychannel
2017-06-11 02:16:12.006 UTC [orderer/main] Deliver -> DEBU eed Starting new Deliver handler
2017-06-11 02:16:12.006 UTC [orderer/common/deliver] Handle -> DEBU eee Starting new deliver loop
2017-06-11 02:16:12.006 UTC [orderer/common/deliver] Handle -> DEBU eef Attempting to read seek info message
2017-06-11 02:16:12.006 UTC [policies] GetPolicy -> DEBU ef0 Returning policy Readers for evaluation
2017-06-11 02:16:12.006 UTC [cauthdsl] func1 -> DEBU ef1 Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> DEBU ef2 Principal evaluation starts: (&{0}) (used [false])
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> ERRO ef3 Principal deserialization failed: (MSP Org2MSP is unknown) for identity [10 7 79 114 103 50 77 83 80 18 217 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 87 122 67 67 65 103 71 103 65 119 73 66 65 103 73 82 65 73 73 98 87 122 83 84 86 43 43 53 73 68 119 74 50 69 99 49 75 65 48 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 120 77 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 73 53 85 81 116 120 80 72 112 48 86 79 113 112 47 121 100 104 65 72 87 55 85 87 76 109 71 116 50 84 97 10 47 79 80 66 117 71 87 99 43 56 74 81 104 117 86 116 114 81 90 47 81 49 105 70 78 113 104 51 54 73 111 122 114 56 53 71 52 55 51 118 82 76 122 112 111 105 88 105 49 104 78 66 50 75 113 106 103 89 48 119 103 89 111 119 10 68 103 89 68 86 82 48 80 65 81 72 47 66 65 81 68 65 103 87 103 77 66 77 71 65 49 85 100 74 81 81 77 77 65 111 71 67 67 115 71 65 81 85 70 66 119 77 66 77 65 119 71 65 49 85 100 69 119 69 66 47 119 81 67 10 77 65 65 119 75 119 89 68 86 82 48 106 66 67 81 119 73 111 65 103 69 43 43 114 55 78 110 110 97 121 54 111 78 67 84 67 113 115 112 51 103 69 56 107 49 121 49 122 84 80 48 121 48 102 56 84 81 110 98 82 105 114 107 119 10 75 65 89 68 86 82 48 82 66 67 69 119 72 52 73 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 89 73 70 99 71 86 108 99 106 69 119 67 103 89 73 75 111 90 73 10 122 106 48 69 65 119 73 68 83 65 65 119 82 81 73 104 65 79 86 118 109 97 97 78 116 73 103 85 83 67 108 51 49 98 97 57 117 68 111 54 66 120 110 73 110 71 67 72 81 49 56 57 122 84 89 116 118 75 110 81 65 105 66 80 10 50 98 81 72 69 51 73 121 83 72 77 106 49 103 98 49 47 47 101 100 108 120 76 112 68 51 56 55 72 88 100 76 84 78 65 69 69 70 79 57 110 103 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> DEBU ef4 Principal evaluation fails: (&{0}) [false]
2017-06-11 02:16:12.007 UTC [cauthdsl] func1 -> DEBU ef5 Gate evaluation fails: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:12.007 UTC [cauthdsl] func1 -> DEBU ef6 Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> DEBU ef7 Principal evaluation starts: (&{0}) (used [false])
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> ERRO ef8 Principal deserialization failed: (MSP Org2MSP is unknown) for identity [10 7 79 114 103 50 77 83 80 18 217 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 87 122 67 67 65 103 71 103 65 119 73 66 65 103 73 82 65 73 73 98 87 122 83 84 86 43 43 53 73 68 119 74 50 69 99 49 75 65 48 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 120 77 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 73 53 85 81 116 120 80 72 112 48 86 79 113 112 47 121 100 104 65 72 87 55 85 87 76 109 71 116 50 84 97 10 47 79 80 66 117 71 87 99 43 56 74 81 104 117 86 116 114 81 90 47 81 49 105 70 78 113 104 51 54 73 111 122 114 56 53 71 52 55 51 118 82 76 122 112 111 105 88 105 49 104 78 66 50 75 113 106 103 89 48 119 103 89 111 119 10 68 103 89 68 86 82 48 80 65 81 72 47 66 65 81 68 65 103 87 103 77 66 77 71 65 49 85 100 74 81 81 77 77 65 111 71 67 67 115 71 65 81 85 70 66 119 77 66 77 65 119 71 65 49 85 100 69 119 69 66 47 119 81 67 10 77 65 65 119 75 119 89 68 86 82 48 106 66 67 81 119 73 111 65 103 69 43 43 114 55 78 110 110 97 121 54 111 78 67 84 67 113 115 112 51 103 69 56 107 49 121 49 122 84 80 48 121 48 102 56 84 81 110 98 82 105 114 107 119 10 75 65 89 68 86 82 48 82 66 67 69 119 72 52 73 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 89 73 70 99 71 86 108 99 106 69 119 67 103 89 73 75 111 90 73 10 122 106 48 69 65 119 73 68 83 65 65 119 82 81 73 104 65 79 86 118 109 97 97 78 116 73 103 85 83 67 108 51 49 98 97 57 117 68 111 54 66 120 110 73 110 71 67 72 81 49 56 57 122 84 89 116 118 75 110 81 65 105 66 80 10 50 98 81 72 69 51 73 121 83 72 77 106 49 103 98 49 47 47 101 100 108 120 76 112 68 51 56 55 72 88 100 76 84 78 65 69 69 70 79 57 110 103 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:16:12.007 UTC [cauthdsl] func2 -> DEBU ef9 Principal evaluation fails: (&{0}) [false]
2017-06-11 02:16:12.007 UTC [cauthdsl] func1 -> DEBU efa Gate evaluation fails: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:12.007 UTC [orderer/common/deliver] Handle -> WARN efb Received unauthorized deliver request for channel mychannel
2017-06-11 02:16:12.007 UTC [orderer/main] func1 -> DEBU efc Closing Deliver stream
2017-06-11 02:16:13.014 UTC [orderer/main] Deliver -> DEBU efd Starting new Deliver handler
2017-06-11 02:16:13.014 UTC [orderer/common/deliver] Handle -> DEBU efe Starting new deliver loop
2017-06-11 02:16:13.014 UTC [orderer/common/deliver] Handle -> DEBU eff Attempting to read seek info message
2017-06-11 02:16:13.015 UTC [policies] GetPolicy -> DEBU f00 Returning policy Readers for evaluation
2017-06-11 02:16:13.015 UTC [cauthdsl] func1 -> DEBU f01 Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:13.016 UTC [cauthdsl] func2 -> DEBU f02 Principal evaluation starts: (&{0}) (used [false])
2017-06-11 02:16:13.016 UTC [cauthdsl] func2 -> ERRO f03 Principal deserialization failed: (MSP Org2MSP is unknown) for identity [10 7 79 114 103 50 77 83 80 18 217 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 87 122 67 67 65 103 71 103 65 119 73 66 65 103 73 82 65 73 73 98 87 122 83 84 86 43 43 53 73 68 119 74 50 69 99 49 75 65 48 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 120 77 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 73 53 85 81 116 120 80 72 112 48 86 79 113 112 47 121 100 104 65 72 87 55 85 87 76 109 71 116 50 84 97 10 47 79 80 66 117 71 87 99 43 56 74 81 104 117 86 116 114 81 90 47 81 49 105 70 78 113 104 51 54 73 111 122 114 56 53 71 52 55 51 118 82 76 122 112 111 105 88 105 49 104 78 66 50 75 113 106 103 89 48 119 103 89 111 119 10 68 103 89 68 86 82 48 80 65 81 72 47 66 65 81 68 65 103 87 103 77 66 77 71 65 49 85 100 74 81 81 77 77 65 111 71 67 67 115 71 65 81 85 70 66 119 77 66 77 65 119 71 65 49 85 100 69 119 69 66 47 119 81 67 10 77 65 65 119 75 119 89 68 86 82 48 106 66 67 81 119 73 111 65 103 69 43 43 114 55 78 110 110 97 121 54 111 78 67 84 67 113 115 112 51 103 69 56 107 49 121 49 122 84 80 48 121 48 102 56 84 81 110 98 82 105 114 107 119 10 75 65 89 68 86 82 48 82 66 67 69 119 72 52 73 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 89 73 70 99 71 86 108 99 106 69 119 67 103 89 73 75 111 90 73 10 122 106 48 69 65 119 73 68 83 65 65 119 82 81 73 104 65 79 86 118 109 97 97 78 116 73 103 85 83 67 108 51 49 98 97 57 117 68 111 54 66 120 110 73 110 71 67 72 81 49 56 57 122 84 89 116 118 75 110 81 65 105 66 80 10 50 98 81 72 69 51 73 121 83 72 77 106 49 103 98 49 47 47 101 100 108 120 76 112 68 51 56 55 72 88 100 76 84 78 65 69 69 70 79 57 110 103 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:16:13.017 UTC [cauthdsl] func2 -> DEBU f04 Principal evaluation fails: (&{0}) [false]
2017-06-11 02:16:13.017 UTC [cauthdsl] func1 -> DEBU f05 Gate evaluation fails: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:13.018 UTC [cauthdsl] func1 -> DEBU f06 Gate evaluation starts: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:13.018 UTC [cauthdsl] func2 -> DEBU f07 Principal evaluation starts: (&{0}) (used [false])
2017-06-11 02:16:13.018 UTC [cauthdsl] func2 -> ERRO f08 Principal deserialization failed: (MSP Org2MSP is unknown) for identity [10 7 79 114 103 50 77 83 80 18 217 6 45 45 45 45 45 66 69 71 73 78 32 45 45 45 45 45 10 77 73 73 67 87 122 67 67 65 103 71 103 65 119 73 66 65 103 73 82 65 73 73 98 87 122 83 84 86 43 43 53 73 68 119 74 50 69 99 49 75 65 48 119 67 103 89 73 75 111 90 73 122 106 48 69 65 119 73 119 99 122 69 76 10 77 65 107 71 65 49 85 69 66 104 77 67 86 86 77 120 69 122 65 82 66 103 78 86 66 65 103 84 67 107 78 104 98 71 108 109 98 51 74 117 97 87 69 120 70 106 65 85 66 103 78 86 66 65 99 84 68 86 78 104 98 105 66 71 10 99 109 70 117 89 50 108 122 89 50 56 120 71 84 65 88 66 103 78 86 66 65 111 84 69 71 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 120 72 68 65 97 66 103 78 86 66 65 77 84 69 50 78 104 10 76 109 57 121 90 122 73 117 90 88 104 104 98 88 66 115 90 83 53 106 98 50 48 119 72 104 99 78 77 84 99 119 78 106 69 120 77 68 69 122 79 84 77 48 87 104 99 78 77 106 99 119 78 106 65 53 77 68 69 122 79 84 77 48 10 87 106 66 98 77 81 115 119 67 81 89 68 86 81 81 71 69 119 74 86 85 122 69 84 77 66 69 71 65 49 85 69 67 66 77 75 81 50 70 115 97 87 90 118 99 109 53 112 89 84 69 87 77 66 81 71 65 49 85 69 66 120 77 78 10 85 50 70 117 73 69 90 121 89 87 53 106 97 88 78 106 98 122 69 102 77 66 48 71 65 49 85 69 65 120 77 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 84 66 90 10 77 66 77 71 66 121 113 71 83 77 52 57 65 103 69 71 67 67 113 71 83 77 52 57 65 119 69 72 65 48 73 65 66 73 53 85 81 116 120 80 72 112 48 86 79 113 112 47 121 100 104 65 72 87 55 85 87 76 109 71 116 50 84 97 10 47 79 80 66 117 71 87 99 43 56 74 81 104 117 86 116 114 81 90 47 81 49 105 70 78 113 104 51 54 73 111 122 114 56 53 71 52 55 51 118 82 76 122 112 111 105 88 105 49 104 78 66 50 75 113 106 103 89 48 119 103 89 111 119 10 68 103 89 68 86 82 48 80 65 81 72 47 66 65 81 68 65 103 87 103 77 66 77 71 65 49 85 100 74 81 81 77 77 65 111 71 67 67 115 71 65 81 85 70 66 119 77 66 77 65 119 71 65 49 85 100 69 119 69 66 47 119 81 67 10 77 65 65 119 75 119 89 68 86 82 48 106 66 67 81 119 73 111 65 103 69 43 43 114 55 78 110 110 97 121 54 111 78 67 84 67 113 115 112 51 103 69 56 107 49 121 49 122 84 80 48 121 48 102 56 84 81 110 98 82 105 114 107 119 10 75 65 89 68 86 82 48 82 66 67 69 119 72 52 73 87 99 71 86 108 99 106 69 117 98 51 74 110 77 105 53 108 101 71 70 116 99 71 120 108 76 109 78 118 98 89 73 70 99 71 86 108 99 106 69 119 67 103 89 73 75 111 90 73 10 122 106 48 69 65 119 73 68 83 65 65 119 82 81 73 104 65 79 86 118 109 97 97 78 116 73 103 85 83 67 108 51 49 98 97 57 117 68 111 54 66 120 110 73 110 71 67 72 81 49 56 57 122 84 89 116 118 75 110 81 65 105 66 80 10 50 98 81 72 69 51 73 121 83 72 77 106 49 103 98 49 47 47 101 100 108 120 76 112 68 51 56 55 72 88 100 76 84 78 65 69 69 70 79 57 110 103 61 61 10 45 45 45 45 45 69 78 68 32 45 45 45 45 45 10]
2017-06-11 02:16:13.018 UTC [cauthdsl] func2 -> DEBU f09 Principal evaluation fails: (&{0}) [false]
2017-06-11 02:16:13.018 UTC [cauthdsl] func1 -> DEBU f0a Gate evaluation fails: (&{n:1 rules:<signed_by:0 > })
2017-06-11 02:16:13.019 UTC [orderer/common/deliver] Handle -> WARN f0b Received unauthorized deliver request for channel mychannel
2017-06-11 02:16:13.029 UTC [orderer/main] func1 -> DEBU f0c Closing Deliver stream
```
Please note: `Org2MSP` disconnected from the channel `mychannel` as expected.
