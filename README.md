# RockPaparScissorsCR

실제 가위바위보 게임에서는 상대방이 어떠한 선택을 할 것인지 예측할 수 없습니다. 하지만 두 사람이 동시에 자신의 선택을 밝히는 것이 아니라 시간 간격을 두고 게임을 한다고 가정하면 상황이 달라집니다. 
  
기본적으로 작성된 가위바위보 컨트랙트상에서 내 선택을 함수로 실행하여 트랜잭션이 발생하면 누구나 Input Data를 볼 수 있게 됩니다. 
   
컨트랙트 상에서 플레이어1의 선택을 플레이어2가 볼 수 있다면 정당한 게임이 될 수 없습니다. 두 플레이어의 선택이 모두 이뤄진 다음에 각 플레이어가 어떠한 선택을 했는지 확인하도록 해야 합니다.
  
단순히 내 선택을 hashing하는 것만으로는 항상 같은 값을 보여주므로 충분하지 않습니다. 따라서 각 플레이어는 본인의 선택(hand)에 본인만의 임시 값(salt)을 더하여 이를 해싱한 값을 commit해야 합니다. 그런 다음 안전한 상태에서 각자의 선택과 임시 값을 다시 보내서 이를 해싱하고 이전에 commit한 값과 비교하여 나의 선택을 reveal하도록 합니다. 
