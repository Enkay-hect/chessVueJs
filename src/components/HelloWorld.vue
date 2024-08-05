<template>
  <div>

  </div>
</template>

<script setup>



        //1
      // const oneMoveForwardRight = startId + width + 1 === targetId 
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild;

      // const twoMoveForwardRight = startId + width * 2 + 2 === targetId 
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild;

      // const threeMoveForwardRight = startId + width * 3 + 3 === targetId
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 3 + 3}"]`).firstElementChild;

      // const fourMoveForwardRight = startId + width * 4 + 4 === targetId
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 3 + 3}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 4 + 4}"]`).firstElementChild;
      
      // const fiveMoveForwardRight = startId + width * 5 + 5 === targetId
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 3 + 3}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 4 + 4}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 5 + 5}"]`).firstElementChild;

      // const sixMoveForwardRight = startId + width * 6 + 6 === targetId
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 3 + 3}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 4 + 4}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 5 + 5}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 6 + 6}"]`).firstElementChild

      // const sevenMoveForwardRight = startId + width * 6 + 6 === targetId
      //     && !document.querySelector(`[square-id="${startId + width + 1}"]`).firstElementChild 
      //     && !document.querySelector(`[square-id="${startId + width * 2 + 2}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 3 + 3}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 4 + 4}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 5 + 5}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 6 + 6}"]`).firstElementChild
      //     && !document.querySelector(`[square-id="${startId + width * 7 + 7}"]`).firstElementChild



        //2
        // const oneMoveForwardLeft = startId - width - 1 === targetId 
        //       && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild;

        // const twoMoveForwardLeft = startId - width * 2 - 2 === targetId 
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild;

        // const threeMoveForwardLeft = startId - width * 3 - 3 === targetId
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 3 - 3}"]`).firstElementChild;

        // const fourMoveForwardLeft = startId - width * 4 - 4 === targetId
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 4 - 4}"]`).firstElementChild;

        // const fiveMoveForwardLeft = startId - width * 5 - 5 === targetId
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 5 - 5}"]`).firstElementChild;

        // const sixMoveForwardLeft = startId - width * 6 - 6 === targetId
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 5 - 5}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 6 - 6}"]`).firstElementChild

        // const sevenMoveForwardLeft = startId - width * 6 - 6 === targetId
        //     && !document.querySelector(`[square-id="${startId - width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId - width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 5 - 5}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 6 - 6}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId - width * 7 - 7}"]`).firstElementChild



        //3
        // const MoveTwo = startId + width - 1 === targetId 
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild;

        // const MoveTwoII = startId + width * 2 - 2 === targetId 
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild;

        // const MoveTwoIII = startId + width * 3 - 3 === targetId
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 3 - 3}"]`).firstElementChild;

        // const MoveTwoIv = startId + width * 4 - 4 === targetId
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 4 - 4}"]`).firstElementChild;

        // const MoveTwoV = startId + width * 5 - 5 === targetId
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 5 - 5}"]`).firstElementChild;

        // const MoveTwoVI = startId + width * 6 - 6 === targetId
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 5 - 5}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 6 - 6}"]`).firstElementChild

        // const MoveTwoVIII = startId + width * 6 - 6 === targetId
        //     && !document.querySelector(`[square-id="${startId + width - 1}"]`).firstElementChild 
        //     && !document.querySelector(`[square-id="${startId + width * 2 - 2}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 3 - 3}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 4 - 4}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 5 - 5}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 6 - 6}"]`).firstElementChild
        //     && !document.querySelector(`[square-id="${startId + width * 7 - 7}"]`).firstElementChild





      // const MoveOne = oneMoveForwardRight || twoMoveForwardRight || threeMoveForwardRight || fourMoveForwardRight || fiveMoveForwardRight || sixMoveForwardRight || sevenMoveForwardRight
      // const MoveForwardLeft = oneMoveForwardLeft || twoMoveForwardLeft || threeMoveForwardLeft || fourMoveForwardLeft || fiveMoveForwardLeft || sixMoveForwardLeft || sevenMoveForwardLeft
      // const MoveThree = MoveTwo || MoveTwoII || MoveTwoIII || MoveTwoIv || MoveTwoV ||MoveTwoVI || MoveTwoVIII
     
      // if(MoveOne || MoveForwardLeft){
      //   return true
      // }










       // if( startId + width + 1 === targetId && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild 
        //     || startId - width - 1 === targetId && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
        //     || startId + width - 1 === targetId && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild 
        //     || startId - width + 1 === targetId && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild

        //     || startId + (width*2) + 2 === targetId && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
        //     || startId - (width*2) - 2 === targetId && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
        //     || startId + (width*2) - 2 === targetId && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
        //     || startId - (width*2) + 2 === targetId && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild


        //     || startId + (width*3 ) + 3 === targetId && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild


        //     // (startId + width * 2 + 2 === targetId && !document.getElementById(targetId).firstElementChild)

        // )






         //     || startId + width * 5 + 5  && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 + 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 + 4}"]`).firstElementChild
      //     || startId + width * 6 + 6  && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 + 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 + 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 5 + 5}"]`).firstElementChild
      //     || startId + width * 7 + 7  && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 + 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 + 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 5 + 5}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 6 + 6}"]`).firstElementChild


      //     || startId - width - 1 === targetId
      //     || startId - width * 2 - 2  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //     || startId - width * 3 - 3  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 - 2}"]`).firstElementChild
      //     || startId - width * 4 - 4  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild
      //     || startId - width * 5 - 5  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 - 4}"]`).firstElementChild
      //     || startId - width * 6 - 6  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 - 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 5 - 5}"]`).firstElementChild
      //     || startId - width * 7 - 7  && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 - 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 5 - 5}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 6 - 6}"]`).firstElementChild


      //     || startId - width + 1 === targetId
      //     || startId - width * 2 + 2  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //     || startId - width * 3 + 3  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 + 2}"]`).firstElementChild
      //     || startId - width * 4 + 4  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 + 3}"]`).firstElementChild
      //     || startId - width * 5 + 5  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 + 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 + 4}"]`).firstElementChild
      //     || startId - width * 6 + 6  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 + 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 5 + 5}"]`).firstElementChild
      //     || startId - width * 7 + 7  && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 2 + 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 4 + 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 5 + 5}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId - width * 6 + 6}"]`).firstElementChild

      //     || startId + width - 1 === targetId
      //     || startId + width * 2 - 2  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //     || startId + width * 3 - 3  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 - 2}"]`).firstElementChild
      //     || startId + width * 4 - 4  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 - 3}"]`).firstElementChild
      //     || startId + width * 5 - 5  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 - 4}"]`).firstElementChild
      //     || startId + width * 6 - 6  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 - 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 5 - 5}"]`).firstElementChild
      //     || startId + width * 7 - 7  && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 2 - 2}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 3 - 3}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 4 - 4}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 5 - 5}"]`).firstElementChild && !document.querySelector(`[square-id = "${startId + width * 6 - 6}"]`).firstElementChild

      //   {
      //   console.log(startId + width + 1);
      //   console.log(targetId);
      //     return true;
      //   }
      // break;


























      // startId + width + 1 === targetId && document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*2) + 2 === targetId && document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*3 ) + 3 === targetId && document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*4 ) + 4 === targetId && document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*5) + 5 === targetId && document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*6) + 6 === targetId && document.querySelector(`[square-id = "${startId + (width*6) + 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
      //       || startId + (width*7) + 7 === targetId && document.querySelector(`[square-id = "${startId + (width*7) + 7}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*6) + 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width + 1}"]`).firstElementChild
            

      //     ||  startId - width - 1 === targetId && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*2) - 2 === targetId && document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*3 ) - 3 === targetId && document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*4 ) - 4 === targetId && document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*5) - 5 === targetId && document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*6) - 6 === targetId && document.querySelector(`[square-id = "${startId - (width*6) - 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId - (width*7) - 7 === targetId && document.querySelector(`[square-id = "${startId - (width*7) - 7}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*6) - 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild 


      //     || startId + width - 1 === targetId && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //       || startId + (width*2) - 2 === targetId && document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width - 1}"]`).firstElementChild
      //       || startId + (width*3 ) - 3 === targetId && document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //       || startId + (width*4 ) - 4 === targetId && document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //       || startId + (width*5) - 5 === targetId && document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //       || startId + (width*6) - 6 === targetId && document.querySelector(`[square-id = "${startId + (width*6) - 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild
      //       || startId + (width*7) - 7 === targetId && document.querySelector(`[square-id = "${startId + (width*7) - 7}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*6) - 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*5) - 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*4) - 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*3) - 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + (width*2) - 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId + width - 1}"]`).firstElementChild 

      //     || startId - width + 1 === targetId && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*2) + 2 === targetId && document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*3 ) + 3 === targetId && document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*4 ) + 4 === targetId && document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*5) + 5 === targetId && document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*6) + 6 === targetId && document.querySelector(`[square-id = "${startId - (width*6) + 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild
      //       || startId - (width*7) + 7 === targetId && document.querySelector(`[square-id = "${startId - (width*7) + 7}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*6) + 6}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*5) + 5}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*4) + 4}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*3) + 3}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - (width*2) + 2}"]`).firstElementChild 
      //           && !document.querySelector(`[square-id = "${startId - width + 1}"]`).firstElementChild

</script>

<style lang="scss" scoped>

</style>