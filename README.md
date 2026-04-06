# PausableContract-9
PausableContract.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PausableContract {
    address public owner;
    bool public paused = false;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner");
        _;
    }

    modifier whenNotPaused() {
        require(!paused, "Contract is paused");
        _;
    }

    function pause() public onlyOwner {
        paused = true;
    }

    function unpause() public onlyOwner {
        paused = false;
    }

    function importantFunction() public whenNotPaused {
        // Logic chính
    }
}
