# Rift-Cape
void PlayerRift(ENetPeer* peer, int colum1, int colum2, int colum3, int colum4, int colum5, int colum6, int berapapacket)
{
	ENetPeer* currentPeer;
	for (currentPeer = server->peers;
		currentPeer < &server->peers[server->peerCount];
		++currentPeer)
	{
		if (currentPeer->state != ENET_PEER_STATE_CONNECTED)
			continue;
		if (isHere(peer, currentPeer))
		{
			if (berapapacket == 2)
			{
				GamePacket p3 = packetEnd(appendIntx(appendIntx(appendString(createPacket(), "OnRiftCape"), colum1), colum2));
				memcpy(p3.data + 8, &(((PlayerInfo*)(peer->data))->netID), 4);
				ENetPacket* packet2 = enet_packet_create(p3.data, p3.len, ENET_PACKET_FLAG_RELIABLE);
				enet_peer_send(currentPeer, 0, packet2);
				delete p3.data;
			}
			else if (berapapacket == 6)
			{
				GamePacket p3 = packetEnd(appendIntx(appendIntx(appendIntx(appendIntx(appendIntx(appendIntx(appendString(createPacket(), "OnRiftCape"), colum1), colum2), colum3), colum4), colum5), colum6));
				memcpy(p3.data + 8, &(((PlayerInfo*)(peer->data))->netID), 4);
				ENetPacket* packet2 = enet_packet_create(p3.data, p3.len, ENET_PACKET_FLAG_RELIABLE);
				enet_peer_send(currentPeer, 0, packet2);
				delete p3.data;
			}
			else
			{

			}
		}
	}
}




//taruh di joinclothesupdate
PlayerRift(peer, 2555, 2402849791, 723421695, 2402849791, 1059267327, 30, 6);
