use common::protocol::*;
use common::entity::EntityType;
use core_protocol::id::GameId;
use serde::{Serialize, Deserialize};

pub fn identify_session() -> String {
	let session_identifier = core_protocol::rpc::ClientRequest::CreateSession{game_id: GameId::Mk48, invitation_id: None, referrer: None, saved_session_tuple: None};

	return serde_json::to_string(&session_identifier).unwrap();
}

pub fn spawn_player() -> String {
	let spawn_command = Command::Spawn(Spawn{entity_type: EntityType::FairmileD});

	return serde_json::to_string(&spawn_command).unwrap();
}

/*pub fn spawn_player() -> String {
	let spawn_command = Command::Spawn(Spawn{entity_type: EntityType::FairmileD});

	return serde_json::to_string(&spawn_command).unwrap();
}*/

pub fn decode_packet(packet: &str) -> Update {
	return serde_json::from_str(packet).unwrap();
}

/*fn identify_session() {
	let session_identifier = core_protocol::rpc::ClientRequest::CreateSession{game_id: GameId::Mk48, invitation_id: None, referrer: None, saved_session_tuple: None};

	let serialized_session_identifier = serde_json::to_string(&session_identifier).unwrap();

	return &serialized_session_identifier[..];
}*/