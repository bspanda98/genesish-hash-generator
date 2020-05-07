hashGenesisBlock = uint256("0x01");
if (true && genesis.GetHash() != hashGenesisBlock)
        {
            printf("Searching for genesis block...\n");
            // This will figure out a valid hash and Nonce if you're
            // creating a different genesis block:
            uint256 hashTarget = CBigNum().SetCompact(genesis.nBits).getuint256();
            uint256 thash;
            
while (true)
{
   thash =genesis.GetHash();
   if (thash <= hashTarget)
             break;
                if ((genesis.nNonce & 0xFFF) == 0)
                {
                    printf("nonce %08X: hash = %s (target = %s)\n", genesis.nNonce, thash.ToString().c_str(), hashTarget.ToString().c_str());
                }
                ++genesis.nNonce;
                if (genesis.nNonce == 0)
                {
                    printf("NONCE WRAPPED, incrementing time\n");
                    ++genesis.nTime;
                }
            }
            printf("genesis.nTime = %u \n", genesis.nTime);
            printf("genesis.nNonce = %u \n", genesis.nNonce);
            printf("genesis.nVersion = %u \n", genesis.nVersion);
            printf("genesis.GetHash = %s\n", genesis.GetHash().ToString().c_str());
            printf("genesis.hashMerkleRoot = %s\n", genesis.hashMerkleRoot.ToString().c_str());
        }
