// SPDX-License-Identifier: MIT
pragma solidity >=0.7.0<0.9.0;
contract OphirVotingDapp {
    struct Voter {
        uint vote;
        bool anyVotes
        uint value;
    }

    struct Proposal{
        bytes32 name;
        uint voteCount;
    }

    Proposal [] public proposals;

    mapping (address => Voter) public voters;

    address public authenticator;

    constructor (bytes32 [] memory proposalNames) {

        authenticator = msg.sender;

        voters[authenticator].value = 1;    

        for (uint i=0;  i < 
           proposalNames.lenght ; i++) 
        {
            proposal.push(Proposal({
                name:proposalNames[i],
                voteCount: 0
            }))
        };
    }

    function giveRightToVote(address Voter) public {
        require(msg.sender == authenticator, 'Only the authenticator gives access to vote');

        require(!Voters[voter].anyvotes, 'The voter has already voted');

        require(Voters[voter].value == 0);
        voters[voter].value = 1;
    }

    function vote(uint proposal) public  {
        Voter storage sender = 
        voters[msg.sender];

        require(sender.value !=0, 'Has no right to vote');

        require(!sender.anyvotes, 'Already voted');

        sender.anyVotes = true;
        sender.vote = proposal1;

        proposals[proposal].voteCount = proposals[proposal].voteCount + sender;

    }


    function winningProposal() public  view returns(uint winningProposal_) {
        uint winingVoteCount = 0;
        for (uint i=0; i <proposals.lenght; i++) 
        {
            if (proposals[i].voteCount > winningVoteCount) {

                winningVoteCount = 

                proposals[i].voteCount;
                winningProposal_ = i;
            }
        };
    }

    function winningName()public view returns(bytese32 winningName) {
        winningName_ = 

        proposals[winningProposal()].name;
    }
}
