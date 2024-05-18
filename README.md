'''
script to convert a single slot rig to a rig that can be used in Unreal Engine
we need to keep the body and head blendshape data so they can be animated
but we want to remove the skinning info so we can re-bind the geo to the UE rig
this contains just the animation skeleton (no def rig)
we want to preserve the blendshape data so we can't just delete history
but if we don't delete history AND we remove the skinCluster connection, the geo might pop back to a different state
instead we will keep the actor's proportions (apply_fitting_data)
and then apply_fitting_data to the incoming source skeleton so the proportions match
then we can transfer the weights
if we restore the characterPose at that point, the geo should change just fine
'''
