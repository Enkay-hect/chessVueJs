<template>
  <div id="gameboard">
    
  </div>

    

  <p>It is <span id="player">black</span>'s turn.</p>
  <p id="info-display"></p>

</template>

<script setup>

import {ref, reactive,  onMounted} from 'vue'
import { king, queen, rook, bishop, pawn, knight }  from '../ScriptServices/pieces.js'


  
const infoDisplay = document.querySelector('#info-display');
const width = 8;

  function createBoard(){

    // const playerDisplay = document.querySelector('#player');
    // playerDisplay.textContent='black'
    
    const gameBoard = document.querySelector('#gameboard');
    
    const startPieces = [
      rook, knight, bishop, queen, king, bishop, knight, rook,
      pawn, pawn, pawn, pawn, pawn, pawn, pawn, pawn,
      '', '', '', '', '', '', '', '',
      '', '', '', '', '', '', '', '',
      '', '', '', '', '', '', '', '',
      '', '', '', '', '', '', '', '',
      pawn, pawn, pawn, pawn, pawn, pawn, pawn, pawn,
      rook, knight, bishop, queen, king, bishop, knight, rook,
    ] 

    startPieces.forEach((startPiece, index) => {
      const square = document.createElement('div');
      square.innerHTML = startPiece

      square.classList.add('square');
      square.firstChild?.setAttribute('draggable', true)
      square.setAttribute('square-id', index)

      const row = Math.floor((63-index)/8)+ 1
      
      if(row % 2 === 0){

        square.classList.add(index % 2 === 0 ? "beige":"brown")

      } else {
        square.classList.add(index % 2 === 0 ? "brown":"beige")

      }

      if(index <= 15){
        square.firstChild.firstElementChild.classList.add('black');
      }

      if(index >= 48){
        square.firstChild.firstElementChild.classList.add('white');
      }

      gameBoard.append(square)
    });
  }

  let startPositionId
  let draggedElement
  let draggedElementId
  // let playerGo

  function addListenersToSquares(){
    const allSquares = document.querySelectorAll("#gameboard .square")
    allSquares.forEach(square =>{
      square.addEventListener('dragstart', dragStart);
      square.addEventListener('dragover', dragOver);
      square.addEventListener('drop', dragDrop);
    })
  }

  function dragStart(e){
   
    startPositionId = e.target.parentNode.getAttribute('square-id');
    draggedElement = e.target
    draggedElementId = e.target.parentNode.getAttribute('square-id');
  }

  function dragOver(e){
    e.preventDefault();
          
  }

  function dragDrop(e){
    e.stopPropagation()

    // console.log(playerGo);
    const playerDisplay = document.querySelector('#player');
    let playerGo = playerDisplay.textContent

    // console.log('playerGo', playerGo);
    // console.log('target' ,e.target);
    
    const correctGo = draggedElement.firstElementChild.classList.contains(playerGo)    
    const taken = e.target.classList.contains('piece')
    const opponentGo = playerGo === 'white' ? 'black' : 'white'
    const valid = checkIfValid(e.target)
    // console.log('opponentGo', opponentGo);

    const takenByOpponent = e.target.firstElementChild?.classList.contains(opponentGo)

    
      if(correctGo){
        if(takenByOpponent && valid){
          const square = e.target.closest('.square');

          const targetPieceContainer = square.querySelector('.piece');

          if (targetPieceContainer && targetPieceContainer.firstElementChild) {
              targetPieceContainer.remove();
          }

          square.appendChild(draggedElement);

          changePlayer();
          return;

       
      }

      if(taken && !takenByOpponent){
        const infoDisplay = document.querySelector('#info-display');
         infoDisplay.textContent = "You cannot go here"
          setTimeout(() => {
            infoDisplay.textContent = ""
          }, 300);
        return
      }

      if(valid){
        e.target.append(draggedElement)
        console.log(draggedElement);
        changePlayer()
      } 

    }

  }


  function checkIfValid(target){
    const targetId = Number(target.getAttribute('square-id') || target.parentNode.getAttribute('square-id'))
    const startId = Number(startPositionId)
    const piece = draggedElement.id


    const playerDisplay = document.querySelector('#player');
    let playerGo = playerDisplay.textContent
    const correctGo = draggedElement.firstElementChild.classList.contains(playerGo)
    const opponentGo = playerGo === 'white' ? 'black' : 'white'    
    const takenByOpponent = target.firstElementChild?.classList.contains(opponentGo)


    switch (piece) {

      case 'pawn':
        const starterRow = [8,9,10,11,12,13,14,15];

        if (
            (starterRow.includes(startId) && startId + width * 2 === targetId )  || 
            (startId + width === targetId && !document.querySelector(`[square-id="${startId + width}"]`).firstElementChild) || 
            (startId + width - 1 === targetId && document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild )  || 
            (startId + width + 1 === targetId && document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild  )
        ) {
          // document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
            return true; 
        } 
        
        break;

      case 'knight' :
        if(  startId + width * 2 + 1 === targetId
          || startId + width * 2 -1 === targetId 

          || startId + width - 2 === targetId
          || startId + width + 2 === targetId
          
          || startId - width * 2 + 1 === targetId
          || startId - width * 2 - 1 === targetId
          
          || startId - width - 2 === targetId
          || startId - width + 2 === targetId

        )
        {
          return true; 
        } 
      break;

      case 'bishop' : 
       if( startId + width + 1 === targetId
            || startId + (width*2) + 2 === targetId  
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*3 ) + 3 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*4 ) + 4 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*5) + 5 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*6) + 6 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*7) + 7 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*6) + 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            

          ||  startId - width - 1 === targetId 
            || startId - (width*2) - 2 === targetId 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*3 ) - 3 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*4 ) - 4 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*5) - 5 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*6) - 6 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*7) - 7 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*6) - 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild 


          || startId + width - 1 === targetId 
            || startId + (width*2) - 2 === targetId  
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*3 ) - 3 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*4 ) - 4 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*5) - 5 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*6) - 6 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*7) - 7 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*6) - 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild 

          || startId - width + 1 === targetId 
            || startId - (width*2) + 2 === targetId  
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*3 ) + 3 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*4 ) + 4 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*5) + 5 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*6) + 6 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*7) + 7 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*6) + 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild

        ){
          return true
        }

      break;
        
      case 'rook':

      if(
            startId + width == targetId
        || startId + (width*2) === targetId 
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        || startId + (width*3) === targetId
            && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        || startId + (width*4) === targetId
            && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        || startId + (width*5) === targetId
            && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        || startId + (width*6) === targetId
            && !document.querySelector(`[square-id = "${startId + (width*5)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        || startId + (width*7) === targetId
            && !document.querySelector(`[square-id = "${startId + (width*6)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*5)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
        
        //...

        ||startId - width == targetId
        || startId - (width*2) === targetId 
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
        || startId - (width*3) === targetId
            && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
        || startId - (width*4) === targetId
            && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
        || startId - (width*5) === targetId
            && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
        || startId - (width*6) === targetId
            && !document.querySelector(`[square-id = "${startId - (width*5)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
        || startId - (width*7) === targetId
            && !document.querySelector(`[square-id = "${startId - (width*6)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*5)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
       
        //..

        || startId + 1 == targetId
        || startId + 2 === targetId 
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
        || startId + 3 === targetId
            && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
        || startId + 4 === targetId
            && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
        || startId + 5 === targetId
            && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
        || startId + 6 === targetId
            && !document.querySelector(`[square-id = "${startId + 5}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
        || startId + 7 === targetId
            && !document.querySelector(`[square-id = "${startId + 6}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 5}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild

        //...


        || startId - 1 == targetId
        || startId - 2 === targetId 
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        || startId - 3 === targetId
            && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        || startId - 4 === targetId
            && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        || startId - 5 === targetId
            && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        || startId - 6 === targetId
            && !document.querySelector(`[square-id = "${startId - 5}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        || startId - 7 === targetId
            && !document.querySelector(`[square-id = "${startId - 6}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 5}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
            && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild

       )
      {
        return true
      }
      break;

      case 'queen':
        if(
          //queen is bishop + rook

          //bishop move
          startId + width + 1 === targetId
            || startId + (width*2) + 2 === targetId  
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*3 ) + 3 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*4 ) + 4 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*5) + 5 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*6) + 6 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            || startId + (width*7) + 7 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*6) + 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            

          ||  startId - width - 1 === targetId 
            || startId - (width*2) - 2 === targetId 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*3 ) - 3 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*4 ) - 4 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*5) - 5 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*6) - 6 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
            || startId - (width*7) - 7 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*6) - 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild 


          || startId + width - 1 === targetId 
            || startId + (width*2) - 2 === targetId  
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*3 ) - 3 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*4 ) - 4 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*5) - 5 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*6) - 6 === targetId  
                && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
            || startId + (width*7) - 7 === targetId 
                && !document.querySelector(`[square-id = "${startId + (width*6) - 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild 

          || startId - width + 1 === targetId 
            || startId - (width*2) + 2 === targetId  
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*3 ) + 3 === targetId 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*4 ) + 4 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*5) + 5 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*6) + 6 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
            || startId - (width*7) + 7 === targetId  
                && !document.querySelector(`[square-id = "${startId - (width*6) + 6}"]`).firstElementChild 
                && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
                    && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
                    && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
                    && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
                    && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild



                //rook move


            ||    startId + width == targetId
            || startId + (width*2) === targetId 
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            || startId + (width*3) === targetId
                && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            || startId + (width*4) === targetId
                && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            || startId + (width*5) === targetId
                && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            || startId + (width*6) === targetId
                && !document.querySelector(`[square-id = "${startId + (width*5)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            || startId + (width*7) === targetId
                && !document.querySelector(`[square-id = "${startId + (width*6)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*5)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + width}"]`).firstElementChild
            
            //...

            ||startId - width == targetId
            || startId - (width*2) === targetId 
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
            || startId - (width*3) === targetId
                && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
            || startId - (width*4) === targetId
                && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
            || startId - (width*5) === targetId
                && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
            || startId - (width*6) === targetId
                && !document.querySelector(`[square-id = "${startId - (width*5)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
            || startId - (width*7) === targetId
                && !document.querySelector(`[square-id = "${startId - (width*6)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*5)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*4)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*3)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - (width*2)}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - width}"]`).firstElementChild
          
            //..

            || startId + 1 == targetId
            || startId + 2 === targetId 
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
            || startId + 3 === targetId
                && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
            || startId + 4 === targetId
                && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
            || startId + 5 === targetId
                && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
            || startId + 6 === targetId
                && !document.querySelector(`[square-id = "${startId + 5}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild
            || startId + 7 === targetId
                && !document.querySelector(`[square-id = "${startId + 6}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 5}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId + 1}"]`).firstElementChild

            //...


            || startId - 1 == targetId
            || startId - 2 === targetId 
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
            || startId - 3 === targetId
                && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
            || startId - 4 === targetId
                && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
            || startId - 5 === targetId
                && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
            || startId - 6 === targetId
                && !document.querySelector(`[square-id = "${startId - 5}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
            || startId - 7 === targetId
                && !document.querySelector(`[square-id = "${startId - 6}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 5}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 4}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 3}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 2}"]`).firstElementChild
                && !document.querySelector(`[square-id = "${startId - 1}"]`).firstElementChild
        ){
            return true
        }
        break;

        case 'king':
          if(
            startId + 1 === targetId
            || startId - 1 === targetId
            || startId + width === targetId
            || startId - width === targetId
            || startId + width -1 === targetId
            || startId + width +1 === targetId
            || startId - width +1 === targetId
            || startId + width -1 === targetId
          ){
            return true
          }
          break;
    }  
  }


function changePlayer(){
        // const infoDisplay = document.querySelector('#info-display');
        const playerDisplay = document.querySelector('#player');
        let playerGo = playerDisplay.textContent

        if(playerGo === "black"){
          reverseIds()
          playerGo = "white"
          playerDisplay.textContent = "white"

        } else {
          revertReverseIds()
          playerGo = "black"
          playerDisplay.textContent = "black" 
        }

      }

      function reverseIds(){
        const width = 8
        const allSquares = document.querySelectorAll(".square");
        allSquares.forEach((square, i) =>{
          square.setAttribute('square-id', (width * width -1) - i)
        })
      }

      function revertReverseIds(){
        const allSquares = document.querySelectorAll(".square");
        allSquares.forEach((square, i) =>{
          square.setAttribute('square-id', i)
        })
      }

      


    onMounted(() => {
      // let playerGo
      createBoard();
      addListenersToSquares();
      // playerGo = 'black'
      
    });


</script>



<style scoped>

  #gameboard{
      height: auto;
      width: 100%;
      display: flex;
      flex-wrap: wrap;
    }
  
  .square{
    height: 40px;
    width: 40px;
    /* background-color: red; */
  }

  .beige{
    background-color: rgb(110, 110, 98);
  }

  .brown{
    background-color: rgb(169, 43, 43);
  }

</style>


