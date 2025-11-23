use std::env;
use common::entity::EntityType;
use bot48::protocol::*;
use serde::{Serialize, Deserialize};

fn main() {
	unsafe {
		EntityType::init();
	}

	// This will crash if you don't give it a JSON object to deserialize, but it works for now.

	let args: Vec<String> = env::args().collect();

	let test = decode_packet(&args[1]);

	println!("test = {:?}", test);
}